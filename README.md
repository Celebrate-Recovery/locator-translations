# Translator Guide - CR Locator

## Welcome Translators! 👋

Thank you for helping make the CR Locator accessible to people around the world. This guide will help you understand how to work with our translation files.

## Supported languages

**26 languages** — 8 reviewed by a native speaker, 18 awaiting review.

| Language              | Code    | Reviewed | Notes             |
| --------------------- | ------- | -------- | ----------------- |
| Afrikaans             | `af`    | Yes      |                   |
| Chinese (Traditional) | `zh-TW` | Yes      |                   |
| English               | `en`    | Yes      |                   |
| Filipino              | `fil`   | Yes      |                   |
| French (Canadian)     | `fr-CA` | Yes      |                   |
| Japanese              | `ja`    | Yes      |                   |
| Portuguese            | `pt`    | Yes      |                   |
| Spanish               | `es`    | Yes      |                   |
| Arabic                | `ar`    | No       |                   |
| Chinese (Simplified)  | `zh-CN` | No       |                   |
| Croatian              | `hr`    | No       |                   |
| Danish                | `da`    | No       |                   |
| Dutch                 | `nl`    | No       |                   |
| French                | `fr`    | No       | Copied from fr-CA |
| German                | `de`    | No       |                   |
| Greek                 | `el`    | No       |                   |
| Indonesian            | `id`    | No       |                   |
| Khmer                 | `km`    | No       |                   |
| Korean                | `ko`    | No       |                   |
| Polish                | `pl`    | No       |                   |
| Romanian              | `ro`    | No       |                   |
| Russian               | `ru`    | No       |                   |
| Swahili               | `sw`    | No       |                   |
| Turkish               | `tr`    | No       |                   |
| Ukrainian             | `uk`    | No       |                   |
| Vietnamese            | `vi`    | No       |                   |

_Reviewed_ = checked or created by a native speaker. Languages marked _No_ were machine-translated and would benefit from review. Details in each locale folder.

## Getting the files from GitHub

You can get the translation files in two ways:

### Option 1: Download as ZIP (no Git required)

1. Open the repository on GitHub (e.g. `https://github.com/Celebrate-Recovery/locator-translations`).
2. Click the green **Code** button.
3. Click **Download ZIP**.
4. Unzip the file on your computer.
5. The locale files are in its own folder (each language has its own folder, e.g. `es`, `fr-CA`, `de`).

To work on a language, open the folder for that language’s code (e.g. `de/` for German). When you’re done, you can share the changed files with the team or submit them via a pull request (upload the modified files in the GitHub web interface).

## File Format

### Structure

Each translation file follows this format:

```yaml
language_code:
  locator:
    shared: # Common translations used everywhere
    layouts: # Header, footer, navigation
    home: # Homepage and search
    results: # Search results pages
  devise: # Sign in and sign up translations
```

### English Comments

**Every line has an English comment** to help you translate:

```yaml
email: Correo electrónico # Email
online: En línea # Online
sunday: Domingo # Sunday
```

**Format:**

```yaml
key: Your Translation # English Reference
```

---

## Translation Guidelines

### 1. Keep the Structure

**DO NOT change:**

- Indentation (spaces)
- Key names (left side of `:`)
- Section organization
- syntax

**Example - DO NOT DO THIS:**

```yaml
# ❌ WRONG - Changed key name
correo_electronico: Correo electrónico # Email

# ✅ CORRECT - Only translate the value
email: Correo electrónico # Email
```

### 2. Variables

Some translations have variables like `%{variable_name}`. **Keep these exactly as they are!**

```yaml
# ✅ CORRECT
none_found_group: "No se encontraron grupos en un radio de %{radius} %{distance_unit}"

# ❌ WRONG - Changed variable names
none_found_group: "No se encontraron grupos en un radio de %{radio} %{unidad}"
```

**Common variables:**

- `%{distance_unit}` - miles or kilometers
- `%{radius}` - search radius number
- `%{location}` - location name
- `%{rep_name}` - representative name

### 3. Quotes

Use quotes when:

- Text contains special characters
- Text contains colons `:`
- Text is a full sentence

```yaml
# ✅ CORRECT
please_enter_location: "Por favor, ingresa una ubicación o código postal."

# ❌ WRONG - Missing quotes with comma
please_enter_location: Por favor, ingresa una ubicación o código postal.
```

### 4. Consistency

Use the same translation for the same English word throughout:

**Example:**
If you translate "Search" as "Buscar", use "Buscar" everywhere, not:

- ❌ "Buscar" in one place
- ❌ "Búsqueda" in another
- ❌ "Investigar" in yet another

**Tip:** Use the `shared` section for common terms!

---

## Common Translation Patterns

### Days of the Week

Three formats are needed:

```yaml
days:
  sunday: Domingo # Full name: Sunday

days_short:
  sunday: Dom # Short: Sun

days_initial:
  sunday: D # Initial: S
```

### Distance Units

```yaml
mile: millas # miles (singular)
kilometer: kilómetros # kilometers (singular)
```

**Note:** Even though it says "miles/kilometers", use the singular form in your language if that's more natural.

### Meeting Formats

```yaml
online: En línea # Online
in_person: En persona # In Person
```

---

## Common Mistakes to Avoid

### ❌ Mistake 1: Changing Indentation

```yaml
# ❌ WRONG
shared:
email: Correo electrónico # Email

# ✅ CORRECT
shared:
  email: Correo electrónico # Email
```

### ❌ Mistake 2: Translating Key Names

```yaml
# ❌ WRONG
correo_electronico: Correo electrónico # Email

# ✅ CORRECT
email: Correo electrónico # Email
```

### ❌ Mistake 3: Removing Variables

```yaml
# ❌ WRONG
none_found_group: "No se encontraron grupos"

# ✅ CORRECT
none_found_group: "No se encontraron grupos en un radio de %{radius} %{distance_unit}"
```

### ❌ Mistake 4: Inconsistent Translations

```yaml
# ❌ WRONG - "Email" translated differently
shared:
  email: Correo electrónico # Email

results:
  partials:
    group:
      email: Email # Email  ← Should be "Correo electrónico"
```

### ❌ Mistake 5: Translating Brand Names

```yaml
# ❌ WRONG
celebrate_recovery: Celebrar la Recuperación

# ✅ CORRECT
celebrate_recovery: Celebrate Recovery
```

---

## Translation Checklist

Before submitting your translation:

- [ ] All English comments are still present
- [ ] No key names were changed
- [ ] All variables (`%{...}`) are preserved
- [ ] Quotes are used where needed
- [ ] Indentation is correct (2 spaces per level)
- [ ] YAML syntax is valid (test with Ruby command)
- [ ] Translations are consistent throughout
- [ ] Cultural appropriateness checked
- [ ] Tested in browser (if possible)

---

## Testing Your Translations

Once you have completed your translations, using the methods below. Most likely you will not need to do the tests yourself as the developer will check the translations for you.

### 1. YAML Syntax Check

After editing, verify the file is valid YAML:

```bash
# In terminal
ruby -ryaml -e "YAML.load_file('config/locales/es/locator/locator.yml')"
```

If no error appears, your syntax is correct! ✅

### 2. View in Browser

```
http://localhost:3000?locale=es
http://localhost:3000?locale=fr
# etc.
```

### 3. Check for Missing Translations

```bash
# In Rails console
I18n.locale = :es
I18n.t('locator.shared.email')
# Should return: "Correo electrónico"
```

---

## Getting Help

### Questions About Context?

Look at the English comments - they show where the text appears:

```yaml
search_placeholder: Búsqueda # Enter a location
# This appears in the search box as placeholder text
```

### Not Sure About a Translation?

1. Check how it's used in the English version
2. Look at the section it's in (`home`, `results`, etc.)
3. Ask a native speaker for review
4. When in doubt, be more formal/respectful

### Technical Issues?

If you get YAML syntax errors:

1. Check indentation (use spaces, not tabs)
2. Check quotes (must be matching pairs)
3. Check colons (space after `:`)
4. Check special characters are escaped

---

## Example: Complete Translation

Here's a complete example showing good translation:

```yaml
es:
  locator:
    shared:
      # Brand & App Names
      cr_locator: Localizador CR # CR Locator
      locator: Localizador # Locator
      celebrate_recovery: Celebrate Recovery # Celebrate Recovery

      # Common Actions
      email: Correo electrónico # Email
      details: Detalles # Details
      search: Búsqueda # Search

      # Meeting Formats
      online: En línea # Online
      in_person: En persona # In Person

      # Days of Week (Full)
      days:
        sunday: Domingo # Sunday
        monday: Lunes # Monday
```

**Notice:**

- ✅ Structure preserved
- ✅ Keys unchanged
- ✅ English comments kept
- ✅ Brand names not translated
- ✅ Consistent terminology
- ✅ Proper indentation

---

## Cultural Considerations

### Formality Level

Choose the appropriate level of formality for your language:

- **Spanish:** Use "tú" or "usted"? (We use "tú" - informal)
- **French:** Use "tu" or "vous"? (We use "vous" - formal)
- **Japanese:** Use casual or polite form? (We use polite form)

### Date/Time Formats

Some languages have different conventions:

- **US English:** Sunday is first day of week
- **Europe:** Monday is first day of week
- **Middle East:** Saturday is first day of week

**Our app:** We list Sunday first, but this is just display order.

### Distance Units

- **US/UK:** Miles
- **Most others:** Kilometers

**Our app:** Automatically shows the right unit based on location.

---

## Resources

### YAML Syntax

- [YAML Official Site](https://yaml.org/)
- [YAML Validator](http://www.yamllint.com/)

### Rails I18n

- [Rails I18n Guide](https://guides.rubyonrails.org/i18n.html)

### Translation Tools

- [DeepL Translator](https://www.deepl.com/) - High quality machine translation
- [Google Translate](https://translate.google.com/) - Quick reference
- **Note:** Always review machine translations!

---

## Thank You! 🙏

Your translation work helps people around the world find freedom and community through Celebrate Recovery. Every translation makes a difference!

**Questions?** Contact the development team or open an issue on GitHub.

---

**Last Updated:** February 26, 2026
**Version:** 2.0 (Optimized Structure)
