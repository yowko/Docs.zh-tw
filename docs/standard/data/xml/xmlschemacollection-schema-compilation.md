---
title: "XmlSchemaCollection 結構描述編譯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="ab183-102">XmlSchemaCollection 結構描述編譯</span><span class="sxs-lookup"><span data-stu-id="ab183-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="ab183-103">**XmlSchemaCollection**快取或程式庫可儲存及驗證 XML 資料精簡 (XDR) 和 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="ab183-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="ab183-104">**XmlSchemaCollection**快取在記憶體中而不是從檔案或 URL 存取它們的結構描述可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="ab183-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab183-105">雖然**XmlSchemaCollection**類別會儲存在 XDR 結構描述和 XML 結構描述，任何方法和屬性或傳回**XmlSchema**物件僅支援 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="ab183-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab183-106"><xref:System.Xml.Schema.XmlSchemaCollection> 類別目前已過時，並已由 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。</span><span class="sxs-lookup"><span data-stu-id="ab183-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="ab183-107">如需有關<xref:System.Xml.Schema.XmlSchemaSet>類別，請參閱[結構描述編譯的 XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="ab183-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="ab183-108">將結構描述加入集合</span><span class="sxs-lookup"><span data-stu-id="ab183-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="ab183-109">結構描述已載入到集合時使用**新增**方法**XmlSchemaCollection**，這時結構描述會與命名空間 URI 相關聯。</span><span class="sxs-lookup"><span data-stu-id="ab183-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="ab183-110">對 XML 結構描述來說，命名空間 URI 通常是結構描述的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab183-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="ab183-111">對 XDR 結構描述來說，命名空間 URI 是當將結構描述加入集合時指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab183-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="ab183-112">檢查集合中的結構描述</span><span class="sxs-lookup"><span data-stu-id="ab183-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="ab183-113">您可以查看結構描述是否在集合中，使用**Contains**方法。</span><span class="sxs-lookup"><span data-stu-id="ab183-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="ab183-114">**Contains**方法會接受**XmlSchema** （適用於 XML 結構描述） 的物件或字串，表示命名空間 URI 相關聯的結構描述 （XML 結構描述和 XDR 結構描述）。</span><span class="sxs-lookup"><span data-stu-id="ab183-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="ab183-115">從集合擷取結構描述</span><span class="sxs-lookup"><span data-stu-id="ab183-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="ab183-116">您也可以使用從集合擷取結構描述**項目**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab183-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="ab183-117">**項目**屬性會接受字串，表示命名空間 URI 相關聯的結構描述，通常其目標命名空間，並傳回**XmlSchema**物件。</span><span class="sxs-lookup"><span data-stu-id="ab183-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="ab183-118">**項目**屬性僅適用於 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="ab183-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="ab183-119">對 XDR 結構描述來說，傳回值永遠是 Null 參考，因為它們並沒有可用的物件模型。</span><span class="sxs-lookup"><span data-stu-id="ab183-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="ab183-120">使用 XmlSchemaCollection 驗證 XML 文件</span><span class="sxs-lookup"><span data-stu-id="ab183-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="ab183-121">您可以驗證 XML 執行個體文件使用**XmlSchemaCollection**藉由建立**XmlSchemaCollection**物件，您的結構描述加入至集合中，並設定**結構描述**屬性**XmlValidatingReader**指派建立**XmlSchemaCollection**至**XmlValidatingReader**。</span><span class="sxs-lookup"><span data-stu-id="ab183-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="ab183-122">提升效能</span><span class="sxs-lookup"><span data-stu-id="ab183-122">Improved Performance</span></span>  
 <span data-ttu-id="ab183-123">建議，如果您要驗證針對相同的結構描述的多個文件，使用**XmlSchemaCollection**因為根據快取在記憶體中的結構描述會提供更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="ab183-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="ab183-124">下列程式碼範例會建立**XmlSchemaCollection**物件、 將結構描述加入至集合中，並設定**結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab183-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab183-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab183-125">See Also</span></span>  
 [<span data-ttu-id="ab183-126">使用 XmlSchemaCollection 的 XDR 驗證</span><span class="sxs-lookup"><span data-stu-id="ab183-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="ab183-127">使用 xmlschemacollection 進行 XML 結構描述 (XSD) 驗證</span><span class="sxs-lookup"><span data-stu-id="ab183-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
