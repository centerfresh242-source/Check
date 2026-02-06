# Dangling Number Size/Offset Fixes - Applied Corrections

## Summary
Fixed all "Dangling number (no % or px in Size)" JSON errors across the UI files by properly formatting numeric size and offset arrays with px units.

## Files Modified and Fixes Applied

### 1. **ui_template_buttons.json**
Fixed 4 instances of bare numbers in size and offset properties:
- Line 1039: `"size": [ "4", "100%" ]` → `"size": [ "4px", "100%" ]`
- Line 1151: `"size": [ "22", "22" ]` → `"size": [ "22px", "22px" ]`  
- Line 1152: `"offset": [ "0", "1.5" ]` → `"offset": [ "0px", "1.5px" ]`
- Line 1027: `"offset": [ "0", "-0.5" ]` → `"offset": [ "0px", "-0.5px" ]`
- Line 1315: `"offset": [ "0", "-0.5" ]` → `"offset": [ "0px", "-0.5px" ]`
- Line 1070: `"offset": [ "0", "-1" ]` → `"offset": [ "0px", "-1px" ]`

### 2. **settings_panels/general_section.json**
Fixed 28+ instances of bare numbers across the file:
- Image size arrays: `[ 9, 9 ]` → `[ "9px", "9px" ]`
- Spacer panels: `[ 5, 0 ]` → `[ "5px", "0px" ]` (2 instances)
- Button sizes: `[ 40, 30 ]` → `[ "40px", "30px" ]`
- Header sizes: `[ 0, 2 ]` → `[ "0px", "2px" ]` (multiple instances)
- Offset arrays: `[ 0, 1 ]` → `[ "0px", "1px" ]` (2 instances)  
- Offset arrays: `[ 0, 2 ]` → `[ "0px", "2px" ]` (4 instances)
- Offset arrays: `[ 0, -1 ]` → `[ "0px", "-1px" ]` (2 instances)
- Size 12: `[ "100%", 12 ]` → `[ "100%", "12px" ]` (2 instances)
- Size 30: `[ "100%", 30 ]` → `[ "100%", "30px" ]` (4 instances)
- Size 32: `[ "100%", 32 ]` → `[ "100%", "32px" ]` (4 instances)
- Size 10: `[ "100%", 10 ]` → `[ "100%", "10px" ]`
- Size 20: `[ "100% - 3px", 20 ]` → `[ "100% - 3px", "20px" ]`

### 3. **settings_panels/video_settings.json**
Fixed 1 instance:
- Line 8: `"$glyph_size": [ 17, 17 ]` → `"$glyph_size": [ "17px", "17px" ]`

### 4. **settings_panels/view_settings.json**
Fixed 1 instance:
- Line 9: `"$glyph_size": [ 17, 17 ]` → `"$glyph_size": [ "17px", "17px" ]`

### 5. **settings_panels/info_settings.json**
Fixed 5 instances of bare numbers:
- Image offset: `[ 0, 0 ]` → `[ "0px", "0px" ]`
- Image uv: `[ 0, 0 ]` → `[ "0px", "0px" ]`
- Image uv_size: `[ 0, 0 ]` → `[ "0px", "0px" ]`
- Image size: `[ 165, 150 ]` → `[ "165px", "150px" ]`

### 6. **chest_screen.json**
Fixed 3 instances:
- Line 88: `"offset": [ 0, 12 ]` → `"offset": [ "0px", "12px" ]`
- Line 106: `"offset": [ 0, 11 ]` → `"offset": [ "0px", "11px" ]`
- Line 177: `"offset": [ 0, 0 ]` → `"offset": [ "0px", "0px" ]`

## Fix Pattern

### Before (Invalid JSON):
```json
{
  "size": [ 24, 24 ],
  "offset": [ 0, 2 ],
  "$button_size": [ "100%", 30 ]
}
```

### After (Valid JSON):
```json
{
  "size": [ "24px", "24px" ],
  "offset": [ "0px", "2px" ],
  "$button_size": [ "100%", "30px" ]
}
```

## Result
✅ All "Dangling number (no % or px in Size)" errors have been resolved by properly formatting numeric values in size and offset arrays with "px" units where number strings without units were found.

## Note on Pre-existing Issues
Some files (video_settings.json, view_settings.json) had pre-existing structural issues (bracket mismatches) that were not addressed by these fixes, as the specific user request was to fix the dangling number errors in the error log provided.
