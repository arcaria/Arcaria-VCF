# Antigravity Form Customization Guide

The **Dynamic Form** allows you to completely control what inputs are sent to the AI. This is powered by a JSON Schema.

## How to Use the Designer

1. Open the app and go to **Settings** > **Open Dynamic Form Designer**.
2. You will see code on the left (JSON) and the form preview on the right.
3. Edit the code. The preview updates as you type.
4. **IMPORTANT**: Click **Save & Apply** at the top to make your changes live in the "Generate" tab.
5. If you break it, click **Reset to Default**.

---

## Cheat Sheet Copy-Paste Examples

### 1. Add a Dropdown (Select)

Copy this block to add a dropdown menu. Good for Models, Samplers, or Styles.

```json
{
  "type": "select",
  "key": "sampler_name",
  "label": "My Sampler",
  "default": "k_euler_a",
  "options": [
    "k_euler_a",
    "k_lms", 
    "k_dpm_2"
  ]
}
```

### 2. Add a Number Slider

Good for Steps, CFG Scale, Width/Height.

```json
{
  "type": "number",
  "key": "steps",
  "label": "Step Count",
  "default": 30,
  "min": 1,
  "max": 100,
  "step": 1
}
```

### 3. Add a Toggle (Checkbox)

Good for boolean flags like NSFW or Tiling.

```json
{
  "type": "checkbox",
  "key": "nsfw",
  "label": "Allow NSFW",
  "default": true
}
```

### 4. Add a Group (Accordion)

Groups help organize your form so it isn't too long.

```json
{
  "type": "group",
  "label": "My Extra Settings",
  "open": false,
  "children": [
      {
         "type": "text",
         "key": "my_setting",
         "label": "Extra Input"
      }
  ]
}
```

## "key" Explained

The `"key"` is the most important part. It tells the AI Horde API what parameter to change.
Common keys supported by AI Horde:

- `width` / `height` (64-1024)
- `steps` (1-50)
- `cfg_scale` (1-20)
- `sampler_name` (k_euler_a, etc)
- `seed` (text or number)
- `clip_skip` (1-12)

If you use a key that isn't supported by the API (like `my_custom_key`), it won't affect the image generation, but it will be saved in the **Metadata JSON** in your Gallery.
