# **Prompt Guide: Plain Text Indented List Format**

## **🎯 DO - Yang Harus Dilakukan**

### **DO Use Consistent Indentation**
```
project/                    # ✅ DO: Use consistent 2 or 4 spaces
  src/                      # ✅ DO: Same indentation for same level
    components/             # ✅ DO: Increase consistently per level
      Button.js
    utils/
      helpers.js
```

### **DO Use Clear Folder/File Markers**
```
foldername/                 # ✅ DO: Use trailing slash for folders
  filename.js               # ✅ DO: No slash for files
  subfolder/                # ✅ DO: Consistent slash usage
    anotherfile.txt
```

### **DO Maintain Sibling Alignment**
```
src/                        # ✅ DO: All level 1 items aligned
  components/               # ✅ DO: All level 2 items aligned  
  utils/                    # ✅ DO: Same level, same indentation
  tests/                    # ✅ DO: Consistent with siblings
config/                     # ✅ DO: Back to level 1 alignment
```

### **DO Use Descriptive Names**
```
ecommerce-platform/         # ✅ DO: Clear, descriptive names
  order-management/         # ✅ DO: Purpose is obvious
    payment-processing/
      credit-card-validation.js
  user-authentication/
    multi-factor-auth/
```

### **DO Keep Logical Grouping**
```
src/                        # ✅ DO: Logical organization
  features/                 # ✅ DO: Related items grouped together
    user/
      profile/
      settings/
    product/
      catalog/
      reviews/
  shared/                   # ✅ DO: Shared resources grouped
    components/
    utils/
```

---

## **🚫 DON'T - Yang Tidak Boleh Dilakukan**

### **DON'T Mix Indentation Styles**
```
project/                    # ❌ DON'T: Mixing space counts
  src/                      # ❌ DON'T: 1 space
    components/             # ❌ DON'T: 2 spaces
        utils/              # ❌ DON'T: 4 spaces suddenly
      tests/                # ❌ DON'T: 2 spaces again - inconsistent!
```

### **DON'T Use Ambiguous Naming**
```
project/                    # ❌ DON'T: Unclear what this is
  folder1/                  # ❌ DON'T: What does folder1 contain?
    stuff/                  # ❌ DON'T: What kind of stuff?
      thing.js              # ❌ DON'T: What does this thing do?
  data/                     # ❌ DON'T: Too generic
    things/                 # ❌ DON'T: Meaningless name
```

### **DON'T Create Unclear Folder/File Distinction**
```
project                     # ❌ DON'T: Is this a folder or file?
  src                       # ❌ DON'T: No slash - confusing
    components              # ❌ DON'T: Folder without slash
      Button.js/            # ❌ DON'T: File with slash - wrong!
    utils.js                # ❌ DON'T: Is this file or folder?
```

### **DON'T Break Sibling Alignment**
```
src/                        # ❌ DON'T: Misaligned siblings
    components/             # ❌ DON'T: Wrong indentation level
  utils/                    # ❌ DON'T: Should be same as components
      tests/                # ❌ DON'T: Completely wrong level
  config/                   # ❌ DON'T: Inconsistent alignment
```

### **DON'T Create Illogical Structure**
```
src/                        # ❌ DON'T: No logical grouping
  user.js                   # ❌ DON'T: Mixed levels without reason
  components/
    auth/
  utils.js
  tests/
    user.test.js
  auth/
    middleware/
  components/
    forms/                  # ❌ DON'T: Duplicate categories scattered
```

---

## **🔄 QUICK REFERENCE: DO vs DON'T**

### **Indentation**
```bash
# ✅ DO THIS:
project/
  src/
    app/
      components/

# ❌ NOT THIS:
project/
 src/
   app/
    components/
```

### **Naming Convention**
```bash
# ✅ DO THIS:
user-management/
  password-reset/
    email-templates/

# ❌ NOT THIS:  
usr_mng/
  pwd_rst/
    eml_tmpl/
```

### **File vs Folder**
```bash
# ✅ DO THIS:
folder/
  file.js
  subfolder/
    anotherfile.txt

# ❌ NOT THIS:
folder
  file.js/
  subfolder
    anotherfile.txt
```

### **Structure Organization**
```bash
# ✅ DO THIS:
src/
  features/
    user/
    product/
  shared/
    components/
    utils/

# ❌ NOT THIS:
src/
  user/
  components/
  product/
  utils/
  user-components/
  product-utils/
```

---

## **📝 PROMPT EXAMPLES FOR AI**

### **When Creating Structure:**
```
"Create a project structure using plain text indented list format with:
- Consistent 2-space indentation
- Clear folder/file markers with trailing slashes for folders
- Descriptive names that indicate purpose
- Logical grouping of related components
- Proper sibling alignment at each level"
```

### **When Fixing Structure:**
```
"Fix this inconsistent directory structure by:
- Standardizing to 2-space indentation per level
- Adding trailing slashes to all folders
- Removing slashes from all files
- Aligning sibling items at the same level
- Using clear, descriptive names"
```

### **When Requesting Analysis:**
```
"Analyze this directory structure and identify:
- Inconsistent indentation patterns
- Missing or incorrect folder/file markers
- Misaligned sibling items
- Unclear or generic naming
- Illogical grouping of components"
```

---

## **🎨 TEMPLATE FOR CORRECT USAGE**

```bash
# ✅ COPY THIS TEMPLATE:

project-name/
  src/
    features/
      feature-one/
        components/
        utils/
        tests/
      feature-two/
        components/
        services/
    shared/
      components/
      hooks/
      utils/
  tests/
    unit/
    integration/
    e2e/
  docs/
    api/
    guides/
  config/
    environments/
      development/
      production/
```

**Remember:** Consistency is key! Choose one style and stick with it throughout your entire structure.
