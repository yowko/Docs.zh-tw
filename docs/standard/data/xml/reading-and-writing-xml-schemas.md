---
title: 讀取及寫入 XML 結構描述
description: 使用架構物件模型 (SOM) API，從 .NET 中的檔案或其他來源讀取和寫入 XML 架構定義語言 (XSD) 架構。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 7ba736272579451cf30c5e78026ffaa4186e03c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686848"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="41220-103">讀取及寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-103">Reading and Writing XML Schemas</span></span>

<span data-ttu-id="41220-104">結構描述物件模型 (SOM) API 可從檔案或其他來源中讀取及寫入 XML 結構描述定義語言 (XSD) 結構描述，並使用 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別 (該命名空間對應於全球資訊網協會 (W3C) XML 結構描述建議事項中所定義的結構) 來建置記憶體中的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="41220-104">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="41220-105">讀取及寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-105">Reading and Writing XML Schemas</span></span>  

 <span data-ttu-id="41220-106"><xref:System.Xml.Schema.XmlSchema> 類別提供 <xref:System.Xml.Schema.XmlSchema.Read%2A> 及 <xref:System.Xml.Schema.XmlSchema.Write%2A> 方法，以讀取及寫入 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="41220-106">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="41220-107"><xref:System.Xml.Schema.XmlSchema.Read%2A> 方法會傳回表示 XML 結構描述的 <xref:System.Xml.Schema.XmlSchema> 物件，並使用選擇性 <xref:System.Xml.Schema.ValidationEventHandler> 做為參數，以處理讀取 XML 結構描述時遇到的結構描述驗證警告及錯誤。</span><span class="sxs-lookup"><span data-stu-id="41220-107">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="41220-108"><xref:System.Xml.Schema.XmlSchema.Write%2A> 方法會將 XML 結構描述寫入 <xref:System.IO.Stream>、<xref:System.IO.TextWriter> 及 <xref:System.Xml.XmlWriter> 物件，並可使用選擇性 <xref:System.Xml.XmlNamespaceManager> 物件做為參數。</span><span class="sxs-lookup"><span data-stu-id="41220-108">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="41220-109"><xref:System.Xml.XmlNamespaceManager> 可用於處理在 XML 結構描述中發現的命名空間。</span><span class="sxs-lookup"><span data-stu-id="41220-109">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="41220-110">如需有關 <xref:System.Xml.XmlNamespaceManager> 類別的詳細資訊，請參閱[管理 XML 文件中的命名空間](managing-namespaces-in-an-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="41220-110">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="41220-111">下列程式碼範例說明在檔案中讀取及寫入 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="41220-111">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="41220-112">該程式碼範例採用 `example.xsd` 檔案，並使用 <xref:System.Xml.Schema.XmlSchema>`static` 方法將其讀取至 <xref:System.Xml.Schema.XmlSchema.Read%2A> 物件，然後將該檔案寫入主控台及新的 `new.xsd` 檔案。</span><span class="sxs-lookup"><span data-stu-id="41220-112">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="41220-113">該程式碼範例還將 <xref:System.Xml.Schema.ValidationEventHandler> 做為參數提供給 `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> 方法，以處理讀取 XML 結構描述時遇到的任何結構描述驗證警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="41220-113">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="41220-114">如果未指定 <xref:System.Xml.Schema.ValidationEventHandler> (`null`)，則不會報告警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="41220-114">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="41220-115">範例會將 `example.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="41220-115">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41220-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41220-116">See also</span></span>

- [<span data-ttu-id="41220-117">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="41220-117">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="41220-118">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-118">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="41220-119">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-119">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="41220-120">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-120">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="41220-121">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="41220-121">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="41220-122">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="41220-122">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="41220-123">後結構描述編譯資訊集</span><span class="sxs-lookup"><span data-stu-id="41220-123">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="41220-124">管理 XML 文件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="41220-124">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
