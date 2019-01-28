---
title: 使用 XPathNavigator 修改 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72cbcf1294f3d13f406d8db177f66fdc367c0758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724443"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="a24e7-102">使用 XPathNavigator 修改 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a24e7-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="a24e7-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供一組可用於修改 XML 文件中節點及值的方法。</span><span class="sxs-lookup"><span data-stu-id="a24e7-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="a24e7-104">為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a24e7-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="a24e7-105">可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。</span><span class="sxs-lookup"><span data-stu-id="a24e7-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a24e7-106">由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="a24e7-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="a24e7-107">如需有關建立可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="a24e7-108">修改節點</span><span class="sxs-lookup"><span data-stu-id="a24e7-108">Modifying Nodes</span></span>  
 <span data-ttu-id="a24e7-109">一種變更節點值的簡單技術是使用 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法。</span><span class="sxs-lookup"><span data-stu-id="a24e7-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="a24e7-110">下表列出了這些方法對不同節點型別的影響。</span><span class="sxs-lookup"><span data-stu-id="a24e7-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="a24e7-111">資料變更</span><span class="sxs-lookup"><span data-stu-id="a24e7-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="a24e7-112">不支援。</span><span class="sxs-lookup"><span data-stu-id="a24e7-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="a24e7-113">項目的內容。</span><span class="sxs-lookup"><span data-stu-id="a24e7-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="a24e7-114">屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a24e7-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="a24e7-115">文字內容。</span><span class="sxs-lookup"><span data-stu-id="a24e7-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="a24e7-116">內容 (目標除外)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="a24e7-117">註解的內容。</span><span class="sxs-lookup"><span data-stu-id="a24e7-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="a24e7-118">不支援。</span><span class="sxs-lookup"><span data-stu-id="a24e7-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a24e7-119">不支援編輯 <xref:System.Xml.XPath.XPathNodeType.Namespace> 節點或 <xref:System.Xml.XPath.XPathNodeType.Root> 節點。</span><span class="sxs-lookup"><span data-stu-id="a24e7-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="a24e7-120"><xref:System.Xml.XPath.XPathNavigator> 類別還提供一組可用於插入及移除節點的方法。</span><span class="sxs-lookup"><span data-stu-id="a24e7-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="a24e7-121">如需有關從n XML 文件插入和移除節點的詳細資訊，請參閱[使用 XPathNavigator 插入 XML 資料](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)和[使用 XPathNavigator 移除 XML 資料](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a24e7-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="a24e7-122">修改不具型別值</span><span class="sxs-lookup"><span data-stu-id="a24e7-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="a24e7-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。</span><span class="sxs-lookup"><span data-stu-id="a24e7-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="a24e7-124">插入的值不具有任何型別，或未根據節點型別 (若提供結構描述資訊) 驗證新值的有效性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="a24e7-125">在下列範例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用於更新 `price` 檔案中的所有 `contosoBooks.xml` 項目。</span><span class="sxs-lookup"><span data-stu-id="a24e7-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="a24e7-126">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="a24e7-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="a24e7-127">修改具型別值</span><span class="sxs-lookup"><span data-stu-id="a24e7-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="a24e7-128">當節點的型別為 W3C XML 結構描述簡單型別時，會根據簡單型別的 Facet，對 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值執行設定前的檢查。</span><span class="sxs-lookup"><span data-stu-id="a24e7-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="a24e7-129">如果根據節點的型別，新值無效 (例如，在型別為 `-1` 的項目上設定 `xs:positiveInteger` 值)，則會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a24e7-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="a24e7-130">下列範例會嘗試將 `price` 檔案中第一個 `book` 項目之 `contosoBooks.xml` 項目的值，變更為 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="a24e7-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="a24e7-131">因為在 `price` 檔案中將 `xs:decimal` 項目的 XML 結構描述型別定義為 `contosoBooks.xsd`，所以這個動作會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a24e7-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="a24e7-132">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="a24e7-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="a24e7-133">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="a24e7-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="a24e7-134">編輯強型別 XML 資料的影響</span><span class="sxs-lookup"><span data-stu-id="a24e7-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="a24e7-135"><xref:System.Xml.XPath.XPathNavigator> 類別使用 W3C XML 結構描述，做為說明強型別 XML 的基礎。</span><span class="sxs-lookup"><span data-stu-id="a24e7-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="a24e7-136">根據對 W3C XML 結構描述文件的驗證，可為項目及屬性加上型別資訊標註。</span><span class="sxs-lookup"><span data-stu-id="a24e7-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="a24e7-137">可包含其他項目或屬性的項目稱為複雜型別，而那些僅包含文字內容的則稱為簡單型別。</span><span class="sxs-lookup"><span data-stu-id="a24e7-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a24e7-138">屬性僅可具有簡單型別。</span><span class="sxs-lookup"><span data-stu-id="a24e7-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="a24e7-139">如果項目或屬性符合其型別定義的所有特定規則，則認為是結構描述有效。</span><span class="sxs-lookup"><span data-stu-id="a24e7-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="a24e7-140">具有簡單型別 `xs:int` 的項目必須包含 -2147483648 與 2147483647 之間的數值，才為結構描述有效。</span><span class="sxs-lookup"><span data-stu-id="a24e7-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="a24e7-141">對於複雜型別，項目的結構描述有效性取決於其項目子系及屬性的結構描述有效性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="a24e7-142">因此，如果項目對其複雜型別定義有效，則其所有項目子系及屬性對其型別定義都有效。</span><span class="sxs-lookup"><span data-stu-id="a24e7-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="a24e7-143">同樣地，如果項目中有一個項目子系或屬性對其型別定義無效或有效性不明，則該項目也會無效或具有不明有效性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="a24e7-144">如果項目的有效性取決於其項目子系及屬性的有效性，則修改任何一項都會導致變更項目的有效性 (如果先前已為有效)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="a24e7-145">特別是當插入、更新或刪除項目的項目子系或屬性時，項目的有效性會變為不明。</span><span class="sxs-lookup"><span data-stu-id="a24e7-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="a24e7-146">此由項目 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性設為 <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> 來表示。</span><span class="sxs-lookup"><span data-stu-id="a24e7-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="a24e7-147">而且，此影響還會按階層向上遞迴處理整個 XML 文件，因為項目的父項目 (及其父項目等) 有效性也會變為不明。</span><span class="sxs-lookup"><span data-stu-id="a24e7-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="a24e7-148">如需結構描述驗證及 <xref:System.Xml.XPath.XPathNavigator> 類別的詳細資訊，請參閱[使用 XPathNavigator 進行結構描述驗證](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="a24e7-149">修改屬性</span><span class="sxs-lookup"><span data-stu-id="a24e7-149">Modifying Attributes</span></span>  
 <span data-ttu-id="a24e7-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法可用於修改不具型別與具型別屬性節點，以及＜修改節點＞一節中列出的其他節點型別。</span><span class="sxs-lookup"><span data-stu-id="a24e7-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="a24e7-151">下列範例會變更 `genre` 檔案中第一個 `book` 項目的 `books.xml` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="a24e7-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="a24e7-152">如需 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法的詳細資訊，請參閱＜修改不具型別值＞與＜修改具型別值＞這兩節。</span><span class="sxs-lookup"><span data-stu-id="a24e7-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="a24e7-153">InnerXml 及 OuterXml 屬性</span><span class="sxs-lookup"><span data-stu-id="a24e7-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="a24e7-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="a24e7-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="a24e7-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。</span><span class="sxs-lookup"><span data-stu-id="a24e7-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="a24e7-156">同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。</span><span class="sxs-lookup"><span data-stu-id="a24e7-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="a24e7-157">下列範例使用 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性來修改 `price` 項目的值，並在 `discount` 檔案中的第一個 `book` 項目上插入新的 `contosoBooks.xml` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="a24e7-158">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="a24e7-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="a24e7-159">修改命名空間節點</span><span class="sxs-lookup"><span data-stu-id="a24e7-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="a24e7-160">在文件物件模型 (DOM) 中，可將命名空間宣告視為可插入、更新及刪除的一般屬性來處理。</span><span class="sxs-lookup"><span data-stu-id="a24e7-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="a24e7-161"><xref:System.Xml.XPath.XPathNavigator> 類別不允許對命名空間節點執行此類作業，原因是變更命名空間節點的值可能會變更命名空間節點範圍內項目及屬性的識別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a24e7-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="a24e7-162">如果上述 XML 範例變更為下列方式，那麼由於變更了每個項目的命名空間 URI 值，所以會有效地重新命名文件中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="a24e7-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="a24e7-163"><xref:System.Xml.XPath.XPathNavigator> 類別允許插入命名空間節點，但這些命名空間節點不可與其插入所在範圍的命名空間宣告衝突。</span><span class="sxs-lookup"><span data-stu-id="a24e7-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a24e7-164">此情況下的命名空間宣告並不是在 XML 文件中的較低範圍處宣告的，因此不會導致重新命名，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a24e7-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="a24e7-165">如果上述 XML 範例變更為下列方式，則命名空間宣告便可在 XML 文件中其他命名空間宣告範圍的下面正確傳播。</span><span class="sxs-lookup"><span data-stu-id="a24e7-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="a24e7-166">在上述 XML 範例中，屬性 `a:parent-id` 是插入在 `parent` 命名空間中的 `http://www.contoso.com/parent-id` 項目上。</span><span class="sxs-lookup"><span data-stu-id="a24e7-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="a24e7-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法用於在定位於 `parent` 項目上時插入屬性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="a24e7-168">`http://www.contoso.com` 類別會自動插入 <xref:System.Xml.XPath.XPathNavigator> 命名空間宣告，以保持 XML 文件其餘內容的一致性。</span><span class="sxs-lookup"><span data-stu-id="a24e7-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="a24e7-169">修改實體參考節點</span><span class="sxs-lookup"><span data-stu-id="a24e7-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="a24e7-170"><xref:System.Xml.XmlDocument> 物件中的實體參考節點是唯讀的，無法使用 <xref:System.Xml.XPath.XPathNavigator> 或 <xref:System.Xml.XmlNode> 類別進行編輯。</span><span class="sxs-lookup"><span data-stu-id="a24e7-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="a24e7-171">任何修改實體參考節點的嘗試都會導致擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="a24e7-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="a24e7-172">修改 xsi:nil 節點</span><span class="sxs-lookup"><span data-stu-id="a24e7-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="a24e7-173">W3C XML 結構描述建議事項中引進了 Nillable 項目的概念。</span><span class="sxs-lookup"><span data-stu-id="a24e7-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="a24e7-174">當項目為 Nillable 時，有可能項目沒有內容但也有效。</span><span class="sxs-lookup"><span data-stu-id="a24e7-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="a24e7-175">Nillable 項目的概念與 `null` 物件的概念類似。</span><span class="sxs-lookup"><span data-stu-id="a24e7-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="a24e7-176">主要區別在於任何方式都無法存取 `null` 物件，而 `xsi:nil` 項目仍具有可存取的屬性 (Property)，如屬性 (Attribute)，但沒有內容 (項目子系或文字)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="a24e7-177">如果 XML 文件中有某個項目的 `xsi:nil` 屬性值為 `true`，則表示該項目沒有內容。</span><span class="sxs-lookup"><span data-stu-id="a24e7-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="a24e7-178">如果使用 <xref:System.Xml.XPath.XPathNavigator> 物件將內容加入至 `xsi:nil` 屬性值為 `true` 的有效項目，則會將其 `xsi:nil` 屬性值設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a24e7-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a24e7-179">對於 `xsi:nil` 屬性設為 `false` 的項目，即使刪除其內容，該屬性的值也不會變更為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a24e7-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="a24e7-180">儲存 XML 文件</span><span class="sxs-lookup"><span data-stu-id="a24e7-180">Saving an XML Document</span></span>  
 <span data-ttu-id="a24e7-181">儲存對 <xref:System.Xml.XmlDocument> 物件所進行的變更 (由本主題中說明的編輯方法所導致) 是使用 <xref:System.Xml.XmlDocument> 類別的方法來執行。</span><span class="sxs-lookup"><span data-stu-id="a24e7-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a24e7-182">如需儲存 <xref:System.Xml.XmlDocument> 物件之變更的詳細資訊，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="a24e7-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24e7-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24e7-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a24e7-184">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a24e7-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a24e7-185">使用 XPathNavigator 插入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a24e7-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="a24e7-186">使用 XPathNavigator 移除 XML 資料</span><span class="sxs-lookup"><span data-stu-id="a24e7-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
