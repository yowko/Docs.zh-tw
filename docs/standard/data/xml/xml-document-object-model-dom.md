---
title: XML 文件物件模型 (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23be7e47dbe54d95eb29ef3b3cb169caeee3eff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579362"
---
# <a name="xml-document-object-model-dom"></a><span data-ttu-id="61b57-102">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="61b57-102">XML Document Object Model (DOM)</span></span>
<span data-ttu-id="61b57-103">XML 文件物件模型 (DOM) 類別是記憶體中 XML 文件的表示法。</span><span class="sxs-lookup"><span data-stu-id="61b57-103">The XML Document Object Model (DOM) class is an in-memory representation of an XML document.</span></span> <span data-ttu-id="61b57-104">DOM 讓您以程式設計方式讀取、管理和修改 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="61b57-104">The DOM allows you to programmatically read, manipulate, and modify an XML document.</span></span> <span data-ttu-id="61b57-105">**XmlReader** 類別也會讀取 XML，但是，它僅提供無快取、順向、唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="61b57-105">The **XmlReader** class also reads XML; however, it provides non-cached, forward-only, read-only access.</span></span> <span data-ttu-id="61b57-106">這表示 **XmlReader** 沒有功能來編輯屬性的值或項目的內容，也沒有插入和移除節點的功能。</span><span class="sxs-lookup"><span data-stu-id="61b57-106">This means that there are no capabilities to edit the values of an attribute or content of an element, or the ability to insert and remove nodes with the **XmlReader**.</span></span> <span data-ttu-id="61b57-107">編輯是 DOM 的主要功能。</span><span class="sxs-lookup"><span data-stu-id="61b57-107">Editing is the primary function of the DOM.</span></span> <span data-ttu-id="61b57-108">雖然在檔案或其他物件中時，實際的 XML 資料是以線性的方式儲存，但 XML 資料呈現在記憶體中卻是常見且結構化的方式。</span><span class="sxs-lookup"><span data-stu-id="61b57-108">It is the common and structured way that XML data is represented in memory, although the actual XML data is stored in a linear fashion when in a file or coming in from another object.</span></span> <span data-ttu-id="61b57-109">下列是 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="61b57-109">The following is XML data.</span></span>  
  
## <a name="input"></a><span data-ttu-id="61b57-110">輸入</span><span class="sxs-lookup"><span data-stu-id="61b57-110">Input</span></span>  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 <span data-ttu-id="61b57-111">下圖顯示當這個 XML 資料讀入 DOM 結構時，如何建立記憶體的結構。</span><span class="sxs-lookup"><span data-stu-id="61b57-111">The following illustration shows how memory is structured when this XML data is read into the DOM structure.</span></span>  
  
 <span data-ttu-id="61b57-112">![XML 文件結構](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span><span class="sxs-lookup"><span data-stu-id="61b57-112">![XML document structure](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span></span>  
<span data-ttu-id="61b57-113">XML 文件結構</span><span class="sxs-lookup"><span data-stu-id="61b57-113">XML document structure</span></span>  
  
 <span data-ttu-id="61b57-114">在 XML 文件結構內，此圖中的每個圓圈表示一個節點，稱為 **XmlNode** 物件。</span><span class="sxs-lookup"><span data-stu-id="61b57-114">Within the XML document structure, each circle in this illustration represents a node, which is called an **XmlNode** object.</span></span> <span data-ttu-id="61b57-115">**XmlNode** 物件是 DOM 樹狀中的基本物件。</span><span class="sxs-lookup"><span data-stu-id="61b57-115">The **XmlNode** object is the basic object in the DOM tree.</span></span> <span data-ttu-id="61b57-116">擴充 **XmlNode** 的 **XmlDocument** 類別支援在文件上整體執行作業的方法，例如，將它載入記憶體或將 XML 儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="61b57-116">The **XmlDocument** class, which extends **XmlNode**, supports methods for performing operations on the document as a whole (for example, loading it into memory or saving the XML to a file.</span></span> <span data-ttu-id="61b57-117">此外，**XmlDocument** 提供一個方法來檢視和管理整個 XML 文件中的節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-117">In addition, **XmlDocument** provides a means to view and manipulate the nodes in the entire XML document.</span></span> <span data-ttu-id="61b57-118">**XmlNode** 和 **XmlDocument** 都可加強效能和可用性，而且有方法和屬性可以：</span><span class="sxs-lookup"><span data-stu-id="61b57-118">Both **XmlNode** and **XmlDocument** have performance and usability enhancements and have methods and properties to:</span></span>  
  
-   <span data-ttu-id="61b57-119">存取和修改 DOM 特定的節點，例如項目節點、實體參考節點等等。</span><span class="sxs-lookup"><span data-stu-id="61b57-119">Access and modify nodes specific to the DOM, such as element nodes, entity reference nodes, and so on.</span></span>  
  
-   <span data-ttu-id="61b57-120">擷取整個節點，除了節點所包含的資訊之外，還有項目節點中的內容。</span><span class="sxs-lookup"><span data-stu-id="61b57-120">Retrieve entire nodes, in addition to the information the node contains, such as the text in an element node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61b57-121">若應用程式不需要 DOM 所提供的結構或編輯功能，則 **XmlReader** 與 **XmlWriter** 類別會提供對 XML 的無快取、順向資料流存取。</span><span class="sxs-lookup"><span data-stu-id="61b57-121">If an application does not require the structure or editing capabilities provided by the DOM, the **XmlReader** and **XmlWriter** classes provide non-cached, forward-only stream access to XML.</span></span> <span data-ttu-id="61b57-122">如需詳細資訊，請參閱 <xref:System.Xml.XmlReader> 與 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="61b57-122">For more information, see <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="61b57-123">**Node** 物件有一組方法和屬性，以及基本且完整定義的特性。</span><span class="sxs-lookup"><span data-stu-id="61b57-123">**Node** objects have a set of methods and properties, as well as basic and well-defined characteristics.</span></span> <span data-ttu-id="61b57-124">這些特性的其中一些是：</span><span class="sxs-lookup"><span data-stu-id="61b57-124">Some of these characteristics are:</span></span>  
  
-   <span data-ttu-id="61b57-125">節點有單一父節點，父節點位於正上方的節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-125">Nodes have a single parent node, a parent node being a node directly above them.</span></span> <span data-ttu-id="61b57-126">唯一沒有父代的節點是文件根，因為它是最上層的節點且包含文件本身與文件片段。</span><span class="sxs-lookup"><span data-stu-id="61b57-126">The only nodes that do not have a parent is the Document root, as it is the top-level node and contains the document itself and document fragments.</span></span>  
  
-   <span data-ttu-id="61b57-127">大多數的節點可以有多重子節點，就是在正下方的節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-127">Most nodes can have multiple child nodes, which are nodes directly below them.</span></span> <span data-ttu-id="61b57-128">下列是可以有子節點的節點型別清單。</span><span class="sxs-lookup"><span data-stu-id="61b57-128">The following is a list of node types that can have child nodes.</span></span>  
  
    -   <span data-ttu-id="61b57-129">**Document**</span><span class="sxs-lookup"><span data-stu-id="61b57-129">**Document**</span></span>  
  
    -   <span data-ttu-id="61b57-130">**DocumentFragment**</span><span class="sxs-lookup"><span data-stu-id="61b57-130">**DocumentFragment**</span></span>  
  
    -   <span data-ttu-id="61b57-131">**EntityReference**</span><span class="sxs-lookup"><span data-stu-id="61b57-131">**EntityReference**</span></span>  
  
    -   <span data-ttu-id="61b57-132">**目**</span><span class="sxs-lookup"><span data-stu-id="61b57-132">**Element**</span></span>  
  
    -   <span data-ttu-id="61b57-133">**屬性**</span><span class="sxs-lookup"><span data-stu-id="61b57-133">**Attribute**</span></span>  
  
     <span data-ttu-id="61b57-134">**XmlDeclaration**、**Notation**、**Entity**、**CDATASection**、**Text**、**Comment**、**ProcessingInstruction** 和 **DocumentType** 節點都沒有子節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-134">The **XmlDeclaration**, **Notation**, **Entity**, **CDATASection**, **Text**, **Comment**, **ProcessingInstruction**, and **DocumentType** nodes do not have child nodes.</span></span>  
  
-   <span data-ttu-id="61b57-135">相同層級的節點，在圖表中以 **book** 和 **pubinfo** 節點呈現，是同層級 (Sibling)。</span><span class="sxs-lookup"><span data-stu-id="61b57-135">Nodes that are at the same level, represented in the diagram by the **book** and **pubinfo** nodes, are siblings.</span></span>  
  
 <span data-ttu-id="61b57-136">DOM 的其中一項特性是它處理屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="61b57-136">One characteristic of the DOM is how it handles attributes.</span></span> <span data-ttu-id="61b57-137">屬性不是父系、子系和同層級關係的節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-137">Attributes are not nodes that are part of the parent, child, and sibling relationships.</span></span> <span data-ttu-id="61b57-138">屬性 (Attribute) 會被視為項目節點的屬性 (Property)，由一個名稱和一個值配對組成。</span><span class="sxs-lookup"><span data-stu-id="61b57-138">Attributes are considered a property of the element node and are made up of a name and a value pair.</span></span> <span data-ttu-id="61b57-139">例如，如果 XML 資料是由與項目 `format="dollar` 關聯的 `price`" 所組成，則 `format` 這個字即為名稱，而 `format` 屬性的值就是 `dollar`。</span><span class="sxs-lookup"><span data-stu-id="61b57-139">For example, if you have XML data consisting of `format="dollar`" associated with the element `price`, the word `format` is the name, and the value of the `format` attribute is `dollar`.</span></span> <span data-ttu-id="61b57-140">若要擷取 **price** 節點的 `format="dollar"` 屬性，可在游標位於 `price` 項目節點上時呼叫 **GetAttribute** 方法。</span><span class="sxs-lookup"><span data-stu-id="61b57-140">To retrieve the `format="dollar"` attribute of the **price** node, you call the **GetAttribute** method when the cursor is located at the `price` element node.</span></span> <span data-ttu-id="61b57-141">如需詳細資訊，請參閱[存取 DOM 中的屬性](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="61b57-141">For more information, see [Accessing Attributes in the DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).</span></span>  
  
 <span data-ttu-id="61b57-142">當 XML 讀入記憶體時，就會建立節點。</span><span class="sxs-lookup"><span data-stu-id="61b57-142">As XML is read into memory, nodes are created.</span></span> <span data-ttu-id="61b57-143">然而，並非所有的節點都是相同型別。</span><span class="sxs-lookup"><span data-stu-id="61b57-143">However, not all nodes are the same type.</span></span> <span data-ttu-id="61b57-144">XML 中的項目之規則和語法與處理指示中的不同。</span><span class="sxs-lookup"><span data-stu-id="61b57-144">An element in XML has different rules and syntax than a processing instruction.</span></span> <span data-ttu-id="61b57-145">因此讀取不同的資料時，會為每個節點指派節點型別。</span><span class="sxs-lookup"><span data-stu-id="61b57-145">Therefore, as various data is read, a node type is assigned to each node.</span></span> <span data-ttu-id="61b57-146">這個節點型別會決定節點的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="61b57-146">This node type determines the characteristics and functionality of the node.</span></span>  
  
 <span data-ttu-id="61b57-147">如需記憶體中所產生之節點型別的詳細資訊，請參閱 [XML 節點的型別](../../../../docs/standard/data/xml/types-of-xml-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="61b57-147">For more information on the types of nodes generated in memory, see [Types of XML Nodes](../../../../docs/standard/data/xml/types-of-xml-nodes.md).</span></span> <span data-ttu-id="61b57-148">如需在節點樹狀結構中建立之物件的詳細資訊，請參閱[將物件階層架構對應至 XML 資料](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="61b57-148">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
 <span data-ttu-id="61b57-149">Microsoft 已擴充 API，使其可在全球資訊網協會 (W3C) DOM 層級 1 和層級 2 中使用，讓您得以更輕鬆地使用 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="61b57-149">Microsoft has extended the APIs that are available in the World Wide Web Consortium (W3C) DOM Level 1 and Level 2 to make it easier to work with an XML document.</span></span> <span data-ttu-id="61b57-150">在完全支援 W3C 標準的同時，其他的類別、方法和屬性增加比使用 W3C XML DOM 所能做的更多的功能。</span><span class="sxs-lookup"><span data-stu-id="61b57-150">While fully supporting the W3C standards, the additional classes, methods, and properties add functionality beyond what can be done using the W3C XML DOM.</span></span> <span data-ttu-id="61b57-151">新類別可讓您存取關聯式資料，提供您同步處理 ADO.NET 資料的方法，同時將資料公開成 XML。</span><span class="sxs-lookup"><span data-stu-id="61b57-151">New classes enable you to access relational data, giving you methods for synchronizing with ADO.NET data, simultaneously exposing data as XML.</span></span> <span data-ttu-id="61b57-152">如需詳細資訊，請參閱[將 DataSet 與 XmlDataDocument 同步處理](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="61b57-152">For more information, see [Synchronizing a DataSet with an XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).</span></span>  
  
 <span data-ttu-id="61b57-153">DOM 對於將 XML 資料讀入記憶體以變更它的結構、加入或移除節點，或修改在項目所包含之內容中的節點所儲存的資料時最有用。</span><span class="sxs-lookup"><span data-stu-id="61b57-153">The DOM is most useful for reading XML data into memory to change its structure, to add or remove nodes, or to modify the data held by a node as in the text contained by an element.</span></span> <span data-ttu-id="61b57-154">但是，在其他案例中，可使用其他比 DOM 更快速的類別。</span><span class="sxs-lookup"><span data-stu-id="61b57-154">However, other classes are available that are faster than the DOM in other scenarios.</span></span> <span data-ttu-id="61b57-155">對於快速、無快取、順向資料流的 XML 存取，請使用 **XmlReader** 與 **XmlWriter**。</span><span class="sxs-lookup"><span data-stu-id="61b57-155">For fast, non-cached, forward-only stream access to XML, use the **XmlReader** and **XmlWriter**.</span></span> <span data-ttu-id="61b57-156">如果您需要具游標模型和 **XPath** 的隨機存取，請使用 **XPathNavigator** 類別。</span><span class="sxs-lookup"><span data-stu-id="61b57-156">If you need random access with a cursor model and **XPath**, use the **XPathNavigator** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b57-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="61b57-157">See Also</span></span>  
 [<span data-ttu-id="61b57-158">XML 節點的類型</span><span class="sxs-lookup"><span data-stu-id="61b57-158">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [<span data-ttu-id="61b57-159">將物件階層對應至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="61b57-159">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
