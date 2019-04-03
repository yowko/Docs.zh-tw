---
title: XML 結構描述物件模型概觀
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdd43f7079563be6b1377f743a84625429ba4f16
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411690"
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="32b95-102">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="32b95-102">XML Schema Object Model Overview</span></span>
<span data-ttu-id="32b95-103">Microsoft .NET Framework 中的結構描述物件模型 (SOM) 是一個豐富的 API，可讓您以程式設計的方式建立、編輯及驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-103">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="32b95-104">SOM 在 XML 結構描述文件上的運作方式，與文件物件模型 (DOM) 在 XML 文件上的運作方式相似。</span><span class="sxs-lookup"><span data-stu-id="32b95-104">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="32b95-105">XML 結構描述文件是有效的 XML 檔案，當它載入 SOM 後，便可傳達符合該結構描述之其他 XML 文件結構及有效性的意義。</span><span class="sxs-lookup"><span data-stu-id="32b95-105">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="32b95-106">結構描述是一個 XML 文件，它會藉由指定特定結構描述之 XML 文件的結構或模型，來定義 XML 文件的類別。</span><span class="sxs-lookup"><span data-stu-id="32b95-106">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="32b95-107">結構描述可識別對 XML 文件內容的條件約束，並說明相容的 XML 文件為了使其特定結構描述有效，而必須使用的字彙 (規則或文法)。</span><span class="sxs-lookup"><span data-stu-id="32b95-107">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="32b95-108">XML 文件的驗證是確保文件符合結構描述所指定之文法的程序。</span><span class="sxs-lookup"><span data-stu-id="32b95-108">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="32b95-109">以下是 .NET Framework 中 SOM API 允許您在建立、編輯及驗證結構描述時所使用的方式。</span><span class="sxs-lookup"><span data-stu-id="32b95-109">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
-   <span data-ttu-id="32b95-110">在檔案間載入及儲存有效的結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-110">Load and save valid schemas to and from files.</span></span>  
  
-   <span data-ttu-id="32b95-111">使用強型別類別建立記憶體中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-111">Create in-memory schemas using strongly typed classes.</span></span>  
  
-   <span data-ttu-id="32b95-112">與 <xref:System.Xml.Schema.XmlSchemaSet> 類別互動，以快取、編譯及擷取結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-112">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
-   <span data-ttu-id="32b95-113">與 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法互動，以根據結構描述驗證 XML 執行個體文件。</span><span class="sxs-lookup"><span data-stu-id="32b95-113">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
-   <span data-ttu-id="32b95-114">建置編輯器以建立及維護結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-114">Build editors for creating and maintaining schemas.</span></span>  
  
-   <span data-ttu-id="32b95-115">動態編輯可編譯和儲存的結構描述，以便在驗證 XML 執行個體文件時使用該結構描述。</span><span class="sxs-lookup"><span data-stu-id="32b95-115">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="32b95-116">結構描述物件模型</span><span class="sxs-lookup"><span data-stu-id="32b95-116">The Schema Object Model</span></span>  
 <span data-ttu-id="32b95-117">SOM 是由 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的大量類別集 (其對應於 XML 結構描述中的項目) 所組成的。</span><span class="sxs-lookup"><span data-stu-id="32b95-117">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="32b95-118">例如，`<xsd:schema>...</xsd:schema>` 項目對應至 <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> 類別，並可使用 `<xsd:schema/>` 類別來表示 <xref:System.Xml.Schema.XmlSchema> 項目可包含的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="32b95-118">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="32b95-119">同樣地，`<xsd:element>...</xsd:element>` 及 `<xsd:attribute>...</xsd:attribute>` 項目分別對應至 <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> 及 <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="32b95-119">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="32b95-120">這種對應關係會在 XML 結構描述的所有項目持續下去，以在 <xref:System.Xml.Schema> 命名空間中建立 XML 結構描述物件模型，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="32b95-120">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 ![System.Xml.Schema 物件模型](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 <span data-ttu-id="32b95-122">如需 <xref:System.Xml.Schema> 命名空間中每個類別的詳細資訊，請參閱 .NET Framework 類別庫中的 <xref:System.Xml.Schema> 命名空間參考文件。</span><span class="sxs-lookup"><span data-stu-id="32b95-122">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b95-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b95-123">See also</span></span>

- [<span data-ttu-id="32b95-124">讀取和寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32b95-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="32b95-125">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32b95-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="32b95-126">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32b95-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="32b95-127">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32b95-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="32b95-128">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="32b95-128">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="32b95-129">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="32b95-129">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="32b95-130">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="32b95-130">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
