---
title: 使用 XPathNavigator 移除 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267059"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="fbe4e-102">使用 XPathNavigator 移除 XML 資料</span><span class="sxs-lookup"><span data-stu-id="fbe4e-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="fbe4e-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供一組可用來從 XML 文件移除節點及值的方法。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="fbe4e-104">為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="fbe4e-105">可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="fbe4e-106">由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="fbe4e-107">如需有關建立可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="fbe4e-108">移除節點</span><span class="sxs-lookup"><span data-stu-id="fbe4e-108">Removing Nodes</span></span>  
 <span data-ttu-id="fbe4e-109"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，以從 XML 文件移除節點。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="fbe4e-110">移除節點</span><span class="sxs-lookup"><span data-stu-id="fbe4e-110">Removing a Node</span></span>  
 <span data-ttu-id="fbe4e-111"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，以從 XML 文件刪除 <xref:System.Xml.XPath.XPathNavigator> 物件目前所位於的目前節點。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="fbe4e-112">在使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法刪除節點之後，就無法從 <xref:System.Xml.XmlDocument> 物件的根存取此節點。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="fbe4e-113">刪除節點之後，<xref:System.Xml.XPath.XPathNavigator> 定位於已刪除節點的父節點上。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="fbe4e-114">刪除作業不會影響定位於已刪除節點上任何 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="fbe4e-115">這些 <xref:System.Xml.XPath.XPathNavigator> 物件是有效的，這表示它們可在已刪除的樹狀子目錄內移動，但無法使用 <xref:System.Xml.XPath.XPathNavigator> 類別的一般節點集巡覽方法，移至主節點樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbe4e-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法可用來將這些 <xref:System.Xml.XPath.XPathNavigator> 物件移回主節點樹狀目錄，或從主節點樹狀目錄移至刪除的樹狀子目錄。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="fbe4e-117">在下列範例中，使用 `price` 方法，刪除 `book` 檔案之第一個 `contosoBooks.xml` 項目的 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 項目。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="fbe4e-118">刪除 <xref:System.Xml.XPath.XPathNavigator> 項目之後，`price` 物件的位置在父 `book` 項目上。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="fbe4e-119">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="fbe4e-120">移除屬性節點</span><span class="sxs-lookup"><span data-stu-id="fbe4e-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="fbe4e-121">使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法，從 XML 文件移除屬性節點。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="fbe4e-122">刪除屬性節點之後，無法再從 <xref:System.Xml.XmlDocument> 物件的根節點存取此節點，而且 <xref:System.Xml.XPath.XPathNavigator> 物件定位於父項目上。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="fbe4e-123">預設屬性</span><span class="sxs-lookup"><span data-stu-id="fbe4e-123">Default Attributes</span></span>  
 <span data-ttu-id="fbe4e-124">無論用來移除屬性的方法為何，對於移除 XML 文件之 DTD 或 XML 結構描述中定義為預設屬性的屬性，都有特殊限制。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="fbe4e-125">除非同時移除其所屬項目，否則無法移除預設屬性。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="fbe4e-126">對於已宣告預設屬性的項目，預設屬性始終存在，因此刪除預設屬性會導致在項目中插入取代屬性，並將其初始化為已宣告的預設值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="fbe4e-127">移除值</span><span class="sxs-lookup"><span data-stu-id="fbe4e-127">Removing Values</span></span>  
 <span data-ttu-id="fbe4e-128"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法，以從 XML 文件移除不具型別值及具型別值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="fbe4e-129">移除不具型別值</span><span class="sxs-lookup"><span data-stu-id="fbe4e-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="fbe4e-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="fbe4e-131">將空字串傳遞至 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法，會移除目前節點的值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="fbe4e-132">下列範例使用 `price` 方法，移除 `book` 檔案中第一個 `contosoBooks.xml` 項目的 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 項目值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="fbe4e-133">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="fbe4e-134">移除具型別值</span><span class="sxs-lookup"><span data-stu-id="fbe4e-134">Removing Typed Values</span></span>  
 <span data-ttu-id="fbe4e-135">當節點的型別為 W3C XML 結構描述簡單型別時，會根據簡單型別的 Facet，對 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值執行設定前的檢查。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="fbe4e-136">如果根據節點的型別，新值無效 (例如，在型別為 `-1` 的項目上設定 `xs:positiveInteger` 值)，則會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="fbe4e-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法也無法將 `null` 當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="fbe4e-138">因此，移除具型別節點的值時必須遵守節點的結構描述型別。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="fbe4e-139">下列範例使用 `price` 方法，將值設為 `book`，來移除 `contosoBooks.xml` 檔案中第一個 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 項目的 `0` 項目值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="fbe4e-140">不會移除節點的值，但是根據書籍之價格的 `xs:decimal` 資料型別，已移除該價格。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="fbe4e-141">命名空間節點</span><span class="sxs-lookup"><span data-stu-id="fbe4e-141">Namespace Nodes</span></span>  
 <span data-ttu-id="fbe4e-142">無法從 <xref:System.Xml.XmlDocument> 物件刪除命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="fbe4e-143">嘗試使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法刪除命名空間節點，會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="fbe4e-144">InnerXml 及 OuterXml 屬性</span><span class="sxs-lookup"><span data-stu-id="fbe4e-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="fbe4e-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="fbe4e-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="fbe4e-147">同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="fbe4e-148">除了本主題中所說明的方法之外，還可以使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性，從 XML 文件移除節點及值。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="fbe4e-149">如需使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性修改節點的詳細資訊，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="fbe4e-150">儲存 XML 文件</span><span class="sxs-lookup"><span data-stu-id="fbe4e-150">Saving an XML Document</span></span>  
 <span data-ttu-id="fbe4e-151">使用 <xref:System.Xml.XmlDocument> 類別的方法，將用本主題中說明之方法對 <xref:System.Xml.XmlDocument> 物件所做的變更儲存下來。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="fbe4e-152">如需儲存 <xref:System.Xml.XmlDocument> 物件之變更的詳細資訊，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="fbe4e-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe4e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbe4e-153">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="fbe4e-154">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="fbe4e-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="fbe4e-155">使用 XPathNavigator 插入 XML 資料</span><span class="sxs-lookup"><span data-stu-id="fbe4e-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="fbe4e-156">使用 XPathNavigator 修改 XML 資料</span><span class="sxs-lookup"><span data-stu-id="fbe4e-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
