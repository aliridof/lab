# **AI-Friendly Tree View Diagram Design**



```
tree
tree -f
```

```
https://raw.githubusercontent.com/aliridof/lab/refs/heads/main/format/tree.md
```

```
📁 ISTILAH-STRUKTUR-POHON/
├── 🌳 01_STRUKTUR_DATA/
│   ├── 📄 hierarchical-data-structure.txt
│   ├── 📄 tree-terminology.txt
│   └── 📄 parent-child-relationship.txt
├── 📁 02_SISTEM_FILE/
│   ├── 📄 directory-tree.txt
│   ├── 📄 file-hierarchy.txt
│   ├── 📄 path-structure.txt
│   └── 📄 navigation-terms.txt
├── 🎨 03_REPRESENTASI_VISUAL/
│   ├── 📄 tree-diagram.txt
│   ├── 📄 dendrogram.txt
│   ├── 📄 indentation-format.txt
│   └── 📄 ascii-art-tree.txt
├── 💻 04_PEMROGRAMAN/
│   ├── 📄 data-serialization.txt
│   ├── 📄 tree-traversal.txt
│   ├── 📄 recursive-structure.txt
│   └── 📄 algorithm-terms.txt
├── 🎯 05_UI_UX/
│   ├── 📄 tree-view-component.txt
│   ├── 📄 hierarchical-list.txt
│   ├── 📄 collapsible-sections.txt
│   └── 📄 information-architecture.txt
├── 🔧 06_TOOLS_IMPLEMENTASI/
│   ├── 📄 command-line-tools.txt
│   ├── 📄 programming-patterns.txt
│   └── 📄 directory-walker.txt
├── 📝 07_DOKUMENTASI/
│   ├── 📄 plain-text-indented-list.txt
│   ├── 📄 markdown-tree-format.txt
│   ├── 📄 ascii-tree-representation.txt
│   └── 📄 standard-formats.txt
├── 🌐 08_WEB_TEKNOLOGI/
│   ├── 📄 dom-tree.txt
│   ├── 📄 xml-document-tree.txt
│   ├── 📄 html-element-tree.txt
│   └── 📄 network-topology.txt
├── 🗂️ 09_ORGANISASI_PROYEK/
│   ├── 📄 project-structure.txt
│   ├── 📄 code-organization.txt
│   ├── 📄 module-hierarchy.txt
│   └── 📄 dependency-tree.txt
├── 🎯 10_ISTILAH_UTAMA/
│   ├── 📄 primary-terms.txt
│   ├── 📄 secondary-terms.txt
│   └── 📄 context-usage.txt
└── 📄 README.txt
```

```
📁 DETAILED-EXPLANATION/
├── 🌳 STRUCTURAL-TERMS/
│   ├── 📄 tree-structure.txt
│   │   └── Struktur data yang menyerupai pohon dengan node dan edge
│   ├── 📄 root-node.txt
│   │   └── Node paling atas yang tidak memiliki parent
│   ├── 📄 leaf-node.txt
│   │   └── Node paling bawah yang tidak memiliki child
│   ├── 📄 parent-child.txt
│   │   └── Hubungan hierarkis antara node
│   └── 📄 sibling-nodes.txt
│       └── Node-node yang berada pada level yang sama
├── 📁 FILE-SYSTEM-TERMS/
│   ├── 📄 directory-tree.txt
│   │   └── Representasi struktur folder dan file
│   ├── 📄 file-hierarchy.txt
│   │   └── Pengorganisasian file dalam level-level
│   ├── 📄 path-structure.txt
│   │   └── Format penulisan lokasi file/direktori
│   └── 📄 nested-directories.txt
│       └── Direktori yang berada di dalam direktori lain
├── 🎨 VISUAL-FORMATS/
│   ├── 📄 tree-diagram.txt
│   │   └── Representasi visual struktur pohon
│   ├── 📄 indentation-format.txt
│   │   └── Format menggunakan spasi/tab untuk menunjukkan level
│   ├── 📄 box-drawing-characters.txt
│   │   └── Karakter Unicode untuk garis dan kotak
│   └── 📄 ascii-art-tree.txt
│       └── Pohon yang digambar menggunakan karakter ASCII
├── 💻 PROGRAMMING-CONCEPTS/
│   ├── 📄 tree-serialization.txt
│   │   └── Konversi struktur pohon ke format data
│   ├── 📄 json-tree.txt
│   │   └── Representasi pohon dalam format JSON
│   ├── 📄 tree-traversal.txt
│   │   └── Metode menelusuri node dalam pohon
│   └── 📄 recursive-structure.txt
│       └── Struktur yang memanggil dirinya sendiri
├── 📝 DOCUMENTATION-FORMATS/
│   ├── 📄 plain-text-indented-list.txt
│   │   └── Format teks dengan indentasi tanpa karakter khusus
│   ├── 📄 markdown-tree.txt
│   │   └── Struktur pohon menggunakan sintaks Markdown
│   └── 📄 standard-formats.txt
│       └── JSON, YAML, XML untuk data hierarkis
└── 🎯 KEY-TERMS/
    ├── 📄 directory-tree-structure.txt
    │   └── ISTILAH UTAMA: Struktur pohon direktori
    ├── 📄 plain-text-indented-list.txt
    │   └── ISTILAH UTAMA: Daftar berindentasi teks biasa
    ├── 📄 tree-view-diagram.txt
    │   └── ISTILAH UTAMA: Diagram tampilan pohon
    ├── 📄 hierarchical-data-format.txt
    │   └── ISTILAH UTAMA: Format data hierarkis
    └── 📄 ascii-tree-representation.txt
        └── ISTILAH UTAMA: Representasi pohon ASCII
```

```
📁 FORMAT-COMPARISON/
├── ✅ RECOMMENDED-FORMATS/
│   ├── 📄 plain-text-indented-list.txt
│   │   ├── Kelebihan: Mudah dibaca AI, universal
│   │   ├── Kekurangan: Kurang visual
│   │   └── Contoh:
│   │       project/
│   │         src/
│   │           app.js
│   ├── 📄 markdown-bullets.txt
│   │   ├── Kelebihan: Native Markdown support
│   │   ├── Kekurangan: Kurang struktur jelas
│   │   └── Contoh:
│   │       - project/
│   │         - src/
│   │           - app.js
│   └── 📄 json-hierarchy.txt
│       ├── Kelebihan: Structured, machine-readable
│       ├── Kekurangan: Overhead untuk manusia
│       └── Contoh:
│           {"project": {"src": {"app.js": "file"}}}
├── ⚠️ LIMITED-USE-FORMATS/
│   ├── 📄 tree-box-characters.txt
│   │   ├── Kelebihan: Visual menarik
│   │   ├── Kekurangan: Sulit untuk AI
│   │   └── Contoh:
│   │       project/
│   │       ├── src/
│   │       │   └── app.js
│   └── 📄 complex-ascii-art.txt
│       ├── Kelebihan: Estetika tinggi
│       ├── Kekurangan: Tidak praktis
│       └── Contoh:
│           +-- project/
│               +-- src/
│                   +-- app.js
└── ❌ NOT-RECOMMENDED/
    ├── 📄 inconsistent-indentation.txt
    │   └── Masalah: Tidak konsisten, sulit diparsing
    ├── 📄 ambiguous-naming.txt
    │   └── Masalah: Nama tidak jelas, membingungkan
    └── 📄 mixed-formats.txt
        └── Masalah: Format campuran, tidak konsisten
```

```
📁 BEST-PRACTICES-GUIDE/
├── ✅ DO-RECOMMENDATIONS/
│   ├── 📄 consistent-indentation.txt
│   │   └── Gunakan 2 atau 4 spasi secara konsisten
│   ├── 📄 clear-naming.txt
│   │   └── Nama deskriptif yang jelas tujuannya
│   ├── 📄 proper-folder-file-markers.txt
│   │   └── Gunakan slash untuk folder, tanpa slash untuk file
│   └── 📄 logical-grouping.txt
│       └── Kelompokkan berdasarkan fungsi, bukan teknologi
├── ❌ DONT-AVOID/
│   ├── 📄 inconsistent-spacing.txt
│   │   └── Jangan campur berbagai jumlah spasi
│   ├── 📄 ambiguous-abbreviations.txt
│   │   └── Hindari singkatan yang tidak jelas
│   ├── 📄 unclear-hierarchy.txt
│   │   └── Jangan buat struktur yang membingungkan
│   └── 📄 mixed-levels.txt
│       └── Hindari mencampur level tanpa pola jelas
├── 🎯 AI-OPTIMIZATION/
│   ├── 📄 machine-readable-format.txt
│   │   └── Format yang mudah diparsing AI
│   ├── 📄 predictable-structure.txt
│   │   └── Struktur yang konsisten dan predictable
│   └── 📄 clear-context.txt
│       └── Berikan konteks yang jelas untuk setiap level
└── 🔧 IMPLEMENTATION-TEMPLATES/
    ├── 📄 web-app-template.txt
    ├── 📄 mobile-app-template.txt
    ├── 📄 api-service-template.txt
    └── 📄 library-package-template.txt
```

```
📁 QUICK-REFERENCE/
├── 🎯 PRIMARY-TERMS/
│   ├── 📌 directory-tree-structure.md
│   ├── 📌 plain-text-indented-list.md
│   ├── 📌 tree-view-diagram.md
│   ├── 📌 hierarchical-data-format.md
│   └── 📌 ascii-tree-representation.md
├── 🔍 CONTEXT-USAGE/
│   ├── 📌 for-developers.md
│   ├── 📌 for-system-admins.md
│   ├── 📌 for-data-scientists.md
│   ├── 📌 for-ui-designers.md
│   └── 📌 for-technical-writers.md
└── 📚 RELATED-CONCEPTS/
    ├── 📌 information-architecture.md
    ├── 📌 data-structures.md
    ├── 📌 file-systems.md
    ├── 📌 user-interface.md
    └── 📌 documentation-standards.md
```

**Keterangan Struktur:**
- `📁` = Folder/Direktori
- `📄` = File teks/penjelasan
- `📌` = File referensi cepat
- `🎯` = Kategori utama
- `✅` = Rekomendasi terbaik
- `⚠️` = Penggunaan terbatas
- `❌` = Tidak direkomendasikan

Struktur di atas mengorganisir semua istilah terkait dalam format tree view yang konsisten dan mudah dipahami!

## **🎯 STRUKTUR OPTIMAL UNTUK AI**

### **Format Terbaik: Hybrid Clean Structure**
```
project-root/
├── src/                    # [APP_LOGIC]
│   ├── components/         # [REUSABLE_UI]
│   ├── pages/              # [ROUTE_COMPONENTS]  
│   └── utils/              # [HELPER_FUNCTIONS]
├── tests/                  # [TEST_SUITES]
├── docs/                   # [DOCUMENTATION]
└── config/                 # [CONFIGURATION]
```

## **📝 DESIGN PRINCIPLES UNTUK AI**

### **1. KONSISTENSI MUTLAK**
```bash
# ✅ AI-Friendly Structure
my-project/
├── source-code/           # [LEVEL_1: DEVELOPMENT]
│   ├── user-interface/    # [LEVEL_2: FRONTEND]
│   ├── api-services/      # [LEVEL_2: BACKEND]
│   └── database/          # [LEVEL_2: DATA_LAYER]
├── quality-assurance/     # [LEVEL_1: TESTING]
│   ├── unit-tests/        # [LEVEL_2: COMPONENT_TEST]
│   ├── integration-tests/ # [LEVEL_2: SYSTEM_TEST]
│   └── test-data/         # [LEVEL_2: TEST_RESOURCES]
└── project-config/        # [LEVEL_1: SETUP]
    ├── environment/       # [LEVEL_2: ENV_CONFIG]
    └── deployment/        # [LEVEL_2: DEPLOY_CONFIG]
```

### **2. PENAMAAN YANG EXPLISIT**
```bash
# ✅ Clear Purpose Naming
ecommerce-platform/
├── order-processing-system/    # [BUSINESS_DOMAIN]
│   ├── payment-validation/     # [SUB_DOMAIN]
│   ├── inventory-management/   # [SUB_DOMAIN]
│   └── shipping-calculation/   # [SUB_DOMAIN]
├── customer-management-system/ # [BUSINESS_DOMAIN]
│   ├── user-authentication/    # [FEATURE]
│   ├── profile-management/     # [FEATURE]
│   └── preference-settings/    # [FEATURE]
└── data-analytics-system/      # [BUSINESS_DOMAIN]
    ├── sales-reports/          # [REPORTING]
    └── customer-insights/      # [ANALYTICS]
```

### **3. LEVEL KEDALAMAN OPTIMAL (4-6 Level)**
```bash
# ✅ Optimal Depth Structure
project/
├── src/                         # [LEVEL_1]
│   ├── features/                # [LEVEL_2]
│   │   ├── authentication/      # [LEVEL_3]
│   │   │   ├── components/      # [LEVEL_4]
│   │   │   ├── services/        # [LEVEL_4]
│   │   │   └── utils/           # [LEVEL_4]
│   │   └── dashboard/           # [LEVEL_3]
│   │       ├── components/      # [LEVEL_4]
│   │       └── analytics/       # [LEVEL_4]
│   └── core/                    # [LEVEL_2]
│       ├── lib/                 # [LEVEL_3]
│       └── constants/           # [LEVEL_3]
└── infrastructure/              # [LEVEL_1]
    ├── ci-cd/                   # [LEVEL_2]
    └── monitoring/              # [LEVEL_2]
```

## **🔧 TEMPLATE UNTUK BERBAGAI JENIS PROYEK**

### **Template 1: Web Application**
```
web-app/
├── frontend/                   # [CLIENT_SIDE]
│   ├── public/                 # [STATIC_ASSETS]
│   ├── src/                    # [SOURCE_CODE]
│   │   ├── components/         # [UI_COMPONENTS]
│   │   ├── pages/              # [ROUTE_PAGES]
│   │   ├── hooks/              # [CUSTOM_HOOKS]
│   │   ├── contexts/           # [STATE_MANAGEMENT]
│   │   └── utils/              # [UTILITY_FUNCTIONS]
│   └── package.json            # [DEPENDENCIES]
├── backend/                    # [SERVER_SIDE]
│   ├── src/                    # [SOURCE_CODE]
│   │   ├── controllers/        # [REQUEST_HANDLERS]
│   │   ├── models/             # [DATA_MODELS]
│   │   ├── routes/             # [API_ROUTES]
│   │   ├── middleware/         # [REQUEST_PROCESSING]
│   │   └── config/             # [APP_CONFIG]
│   └── package.json            # [DEPENDENCIES]
├── shared/                     # [SHARED_CODE]
│   ├── types/                  # [TYPE_DEFINITIONS]
│   └── utils/                  # [CROSS_PLATFORM_UTILS]
└── docker-compose.yml          # [CONTAINER_CONFIG]
```

### **Template 2: Mobile App (React Native)**
```
mobile-app/
├── android/                    # [ANDROID_PLATFORM]
├── ios/                        # [IOS_PLATFORM]
├── src/                        # [CROSS_PLATFORM_CODE]
│   ├── app/                    # [APP_CORE]
│   ├── features/               # [FEATURE_MODULES]
│   │   ├── auth/               # [AUTHENTICATION]
│   │   ├── profile/            # [USER_PROFILE]
│   │   ├── home/               # [MAIN_SCREEN]
│   │   └── settings/           # [APP_SETTINGS]
│   ├── navigation/             # [APP_NAVIGATION]
│   ├── store/                  # [STATE_MANAGEMENT]
│   ├── services/               # [API_SERVICES]
│   ├── utils/                  # [HELPERS]
│   └── assets/                 # [APP_ASSETS]
├── __tests__/                  # [TEST_FILES]
└── package.json                # [DEPENDENCIES]
```

### **Template 3: API Service**
```
api-service/
├── src/                        # [SOURCE_CODE]
│   ├── app/                    # [APPLICATION_CORE]
│   │   ├── middleware/         # [REQUEST_PIPELINE]
│   │   └── config/             # [APP_CONFIGURATION]
│   ├── modules/                # [BUSINESS_MODULES]
│   │   ├── users/              # [USER_MANAGEMENT]
│   │   ├── products/           # [PRODUCT_CATALOG]
│   │   └── orders/             # [ORDER_PROCESSING]
│   ├── shared/                 # [SHARED_RESOURCES]
│   │   ├── database/           # [DATA_ACCESS]
│   │   ├── utils/              # [COMMON_UTILITIES]
│   │   └── types/              # [TYPE_DEFINITIONS]
│   └── main.ts                 # [APP_ENTRYPOINT]
├── tests/                      # [TEST_SUITES]
│   ├── unit/                   # [UNIT_TESTS]
│   ├── integration/            # [INTEGRATION_TESTS]
│   └── fixtures/               # [TEST_DATA]
├── docs/                       # [DOCUMENTATION]
│   ├── api/                    # [API_DOCS]
│   └── deployment/             # [DEPLOYMENT_GUIDE]
└── package.json                # [DEPENDENCIES]
```

## **🎨 STRUKTUR DENGAN KATEGORI EXPLISIT**

### **Enhanced AI-Friendly Structure**
```
[PROJECT_NAME]/
├── [DEVELOPMENT]/              # {CATEGORY: CODE}
│   ├── [FRONTEND]/             # {SUBCATEGORY: CLIENT}
│   ├── [BACKEND]/              # {SUBCATEGORY: SERVER}
│   └── [SHARED]/               # {SUBCATEGORY: COMMON}
├── [TESTING]/                  # {CATEGORY: QUALITY}
│   ├── [UNIT_TESTS]/           # {TYPE: COMPONENT}
│   ├── [INTEGRATION_TESTS]/    # {TYPE: SYSTEM}
│   └── [TEST_DATA]/            # {TYPE: RESOURCES}
├── [DOCUMENTATION]/            # {CATEGORY: DOCS}
│   ├── [API_DOCS]/             # {TYPE: REFERENCE}
│   ├── [USER_GUIDES]/          # {TYPE: TUTORIAL}
│   └── [DEPLOYMENT]/           # {TYPE: OPERATIONS}
├── [CONFIGURATION]/            # {CATEGORY: SETUP}
│   ├── [ENVIRONMENT]/          # {TYPE: ENV_CONFIG}
│   ├── [BUILD_TOOLS]/          # {TYPE: BUILD_CONFIG}
│   └── [DEPLOYMENT]/           # {TYPE: DEPLOY_CONFIG}
└── [ASSETS]/                   # {CATEGORY: RESOURCES}
    ├── [IMAGES]/               # {TYPE: MEDIA}
    ├── [STYLES]/               # {TYPE: DESIGN}
    └── [FONTS]/                # {TYPE: TYPOGRAPHY}
```

## **🚫 STRUKTUR YANG HARUS DIHINDARI**

### **Poor AI-Friendly Structure**
```bash
# ❌ DON'T: Unclear, inconsistent
myproj/
├── stuff/              # ❌ Meaningless name
├── src/
│   ├── comp/           # ❌ Abbreviated unclear
│   │   ├── btn/        # ❌ Too short
│   │   └── frm/        # ❌ Unclear abbreviation
│   ├── utl/            # ❌ Inconsistent naming
│   └── tests/          # ❌ Mixed with source code
├── cfg/                # ❌ Unclear abbreviation
└── readme              # ❌ Missing extension
```

## **📊 CONTOH IMPLEMENTASI NYATA**

### **Real-World E-commerce Platform**
```
ecommerce-platform/
├── storefront/                    # [CLIENT_FACING]
│   ├── web-app/                   # [WEBSITE]
│   └── mobile-app/                # [MOBILE_APPS]
├── backend-services/              # [SERVER_SIDE]
│   ├── product-service/           # [PRODUCT_CATALOG]
│   ├── order-service/             # [ORDER_MANAGEMENT]
│   ├── user-service/              # [USER_MANAGEMENT]
│   ├── payment-service/           # [PAYMENT_PROCESSING]
│   └── inventory-service/         # [STOCK_MANAGEMENT]
├── data-pipeline/                 # [DATA_PROCESSING]
│   ├── analytics-collection/      # [DATA_COLLECTION]
│   ├── etl-processes/             # [DATA_TRANSFORMATION]
│   └── reporting/                 # [DATA_ANALYTICS]
├── infrastructure/                # [OPERATIONS]
│   ├── kubernetes/                # [CONTAINER_MANAGEMENT]
│   ├── monitoring/                # [SYSTEM_MONITORING]
│   └── ci-cd/                     # [AUTOMATED_DEPLOYMENT]
└── documentation/                 # [KNOWLEDGE_BASE]
    ├── api-reference/             # [DEVELOPER_DOCS]
    ├── user-guides/               # [END_USER_DOCS]
    └── deployment-guides/         # [OPERATIONS_DOCS]
```

## **🎯 BEST PRACTICES SUMMARY**

1. **Gunakan kategori eksplisit** dalam penamaan
2. **Batasi kedalaman** maksimal 6 level
3. **Gunakan konsistensi mutlak** dalam indentasi
4. **Hindari singkatan** yang tidak jelas
5. **Kelompokkan berdasarkan fungsi**, bukan teknologi
6. **Gunakan format hybrid** yang clean dan konsisten
7. **Tambahkan komentar kategori** untuk konteks tambahan

Struktur di atas dioptimalkan agar AI dapat dengan mudah:
- Memahami hubungan hierarkis
- Mengidentifikasi tujuan setiap komponen
- Memetakan dependencies
- Menganalisis arsitektur keseluruhan

Berikut **istilah-istilah terkait** format struktur pohon dan tree view diagram yang telah kita bahas:

## 🌳 **ISTILAH TEKNIS STRUKTUR DATA**

### **1. Hierarchical Data Structure**
- **Tree Structure**: Struktur data pohon
- **Root Node**: Node akar/puncak
- **Leaf Node**: Node daun/ujung
- **Parent-Child Relationship**: Hubungan induk-anak
- **Sibling Nodes**: Node saudara selevel
- **Depth/Level**: Kedalaman level
- **Subtree**: Anak pohon

### **2. Tree Terminology**
- **Node/Vertex**: Simpul dalam pohon
- **Edge**: Hubungan antara node
- **Branch**: Cabang dari pohon
- **Forest**: Kumpulan pohon
- **Binary Tree**: Pohon biner
- **N-ary Tree**: Pohon dengan N anak

## 📁 **ISTILAH FILE SYSTEM & DIRECTORY**

### **3. File System Concepts**
- **Directory Tree**: Pohon direktori
- **File Hierarchy**: Hierarki file
- **Path Structure**: Struktur path
- **Nested Directories**: Direktori bersarang
- **Directory Listing**: Daftar direktori

### **4. Navigation Terms**
- **Absolute Path**: Path absolut
- **Relative Path**: Path relatif
- **Current Directory**: Direktori saat ini
- **Parent Directory**: Direktori induk
- **Working Directory**: Direktori kerja

## 🎨 **ISTILAH VISUAL REPRESENTATION**

### **5. Visualization Formats**
- **Tree Diagram**: Diagram pohon
- **Dendrogram**: Diagram dendrogram
- **Indentation**: Penjorokan/indentasi
- **Box-drawing Characters**: Karakter gambar kotak
- **ASCII Art**: Seni ASCII

### **6. Display Styles**
- **Vertical Tree**: Pohon vertikal
- **Horizontal Tree**: Pohon horizontal
- **Collapsible Tree**: Pohon bisa dilipat
- **Interactive Tree**: Pohon interaktif

## 💻 **ISTILAH PROGRAMMING & DEVELOPMENT**

### **7. Data Serialization**
- **Tree Serialization**: Serialisasi pohon
- **JSON Tree**: Pohon dalam format JSON
- **XML Tree**: Pohon dalam format XML
- **YAML Hierarchy**: Hierarki YAML

### **8. Algorithm Terms**
- **Tree Traversal**: Penelusuran pohon
- **Depth-First Search (DFS):** Penelusuran depth-first
- **Breadth-First Search (BFS):** Penelusuran breadth-first
- **Recursive Structure**: Struktur rekursif

## 📊 **ISTILAH UI/UX & INFORMATION ARCHITECTURE**

### **9. User Interface Terms**
- **Tree View**: Tampilan pohon
- **Outline View**: Tampilan outline
- **Hierarchical List**: Daftar hierarkis
- **Collapsible Sections**: Bagian bisa dilipat

### **10. Information Architecture**
- **Taxonomy**: Taksonomi
- **Ontology**: Ontologi
- **Sitemap**: Peta situs
- **Content Hierarchy**: Hierarki konten

## 🔧 **ISTILAH TOOLS & IMPLEMENTATION**

### **11. Command Line Tools**
- **`tree` command**: Perintah tree
- **`find` command**: Perintah find
- **`ls -R`**: List recursive
- **Directory Walker**: Penjelajah direktori

### **12. Programming Concepts**
- **Composite Pattern**: Pola komposit
- **Visitor Pattern**: Pola visitor
- **Recursive Data Structure**: Struktur data rekursif
- **Nested Objects**: Objek bersarang

## 📝 **ISTILAH DOCUMENTATION & FORMATS**

### **13. Documentation Formats**
- **Plain Text Indented List**: Daftar berindentasi teks biasa
- **Markdown Tree**: Pohon Markdown
- **ASCII Tree**: Pohon ASCII
- **Unicode Box-drawing**: Gambar kotak Unicode

### **14. Standard Formats**
- **JSON Format**: Format JSON
- **YAML Format**: Format YAML
- **TOML Structure**: Struktur TOML
- **INI Section Hierarchy**: Hierarki section INI

## 🌐 **ISTILAH WEB & NETWORK**

### **15. Web Technologies**
- **DOM Tree**: Pohon DOM
- **XML Document Tree**: Pohon dokumen XML
- **HTML Element Tree**: Pohon elemen HTML
- **CSS Inheritance Tree**: Pohon pewarisan CSS

### **16. Network Structures**
- **Network Topology**: Topologi jaringan
- **Directory Services**: Layanan direktori
- **LDAP Tree**: Pohon LDAP
- **DNS Hierarchy**: Hierarki DNS

## 🗂️ **ISTILAH PROJECT ORGANIZATION**

### **17. Software Architecture**
- **Project Structure**: Struktur proyek
- **Code Organization**: Organisasi kode
- **Module Hierarchy**: Hierarki modul
- **Package Structure**: Struktur package

### **18. Build Systems**
- **Dependency Tree**: Pohon dependensi
- **Build Hierarchy**: Hierarki build
- **Module Graph**: Grafik modul
- **Component Tree**: Pohon komponen

## 🎯 **ISTILAH YANG PALING RELEVAN UNTUK FORMAT KITA**

### **Primary Terms:**
1. **Directory Tree Structure** - Struktur pohon direktori
2. **Plain Text Indented List** - Daftar berindentasi teks biasa  
3. **Tree View Diagram** - Diagram tampilan pohon
4. **Hierarchical Data Format** - Format data hierarkis
5. **ASCII Tree Representation** - Representasi pohon ASCII

### **Secondary Terms:**
6. **Nested Folder Structure** - Struktur folder bersarang
7. **Visual Directory Map** - Peta direktori visual
8. **File System Hierarchy** - Hierarki sistem file
9. **Project Directory Layout** - Tata letak direktori proyek
10. **Codebase Structure Diagram** - Diagram struktur codebase

## 🔍 **KONTEKS PENGGUNAAN ISTILAH**

- **Untuk Developer**: "Project directory structure"
- **Untuk System Admin**: "File system hierarchy" 
- **Untuk Data Scientist**: "Tree data structure"
- **Untuk UI Designer**: "Tree view component"
- **Untuk Technical Writer**: "Hierarchical documentation"

Istilah-istilah ini membantu dalam komunikasi teknis yang tepat ketika mendiskusikan struktur organisasi file, direktori, atau data hierarkis lainnya.
