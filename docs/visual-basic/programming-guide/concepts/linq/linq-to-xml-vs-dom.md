---
title: "LINQ to XML 比較DOM (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 73aef4ddf4b53297e31d9b8b763dc1cafbef5170
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="d6c24-102">LINQ to XML 比較DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6c24-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="d6c24-103">本節說明一些重要差異[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]和目前佔優勢的 XML 程式設計 API，W3C 文件物件模型 (DOM)。</span><span class="sxs-lookup"><span data-stu-id="d6c24-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="d6c24-104">建構 XML 樹狀的新方式</span><span class="sxs-lookup"><span data-stu-id="d6c24-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="d6c24-105">在 W3C DOM 中，您可以從下往上建置 XML 樹狀；也就是說，您可以建立文件、建立項目，然後將項目加入到文件中。</span><span class="sxs-lookup"><span data-stu-id="d6c24-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="d6c24-106">例如，下列會建立使用 Microsoft 的 DOM 實作， <xref:System.Xml.XmlDocument>::</xref:System.Xml.XmlDocument> XML 樹狀結構的典型方式</span><span class="sxs-lookup"><span data-stu-id="d6c24-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 <span data-ttu-id="d6c24-107">這個編碼樣式在視覺上不會提供太多 XML 樹狀的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6c24-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-108">支援這個方法來建構 XML 樹狀結構，但是也支援替代方法，*功能結構*。</span><span class="sxs-lookup"><span data-stu-id="d6c24-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="d6c24-109">在 Visual Basic 功能結構會使用 XML 常值來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d6c24-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="d6c24-110">以下是您使用建構相同的 XML 樹狀結構的方式[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]功能結構︰</span><span class="sxs-lookup"><span data-stu-id="d6c24-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] functional construction:</span></span>  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="d6c24-111">請注意，將要建構 XML 樹狀結構的程式碼縮排可顯示基礎 XML 的結構。</span><span class="sxs-lookup"><span data-stu-id="d6c24-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="d6c24-112">如需詳細資訊，請參閱[建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c24-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="d6c24-113">直接使用 XML 項目</span><span class="sxs-lookup"><span data-stu-id="d6c24-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="d6c24-114">當您使用 XML 進行程式設計時，您的主要焦點通常是 XML 項目，也可能是屬性。</span><span class="sxs-lookup"><span data-stu-id="d6c24-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="d6c24-115">在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，您可以直接使用 XML 項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="d6c24-115">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="d6c24-116">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="d6c24-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="d6c24-117">完全不使用文件物件來建立 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="d6c24-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="d6c24-118">當您必須使用 XML 樹狀結構的片段時，這可以簡化程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="d6c24-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="d6c24-119">從 XML 檔案直接載入 `T:System.Xml.Linq.XElement` 物件。</span><span class="sxs-lookup"><span data-stu-id="d6c24-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="d6c24-120">將 `T:System.Xml.Linq.XElement` 物件序列化為檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="d6c24-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="d6c24-121">將這個 XML 項目或屬性與 W3C DOM 相比較，後者中的 XML 文件會當做 XML 樹狀結構的邏輯容器使用。</span><span class="sxs-lookup"><span data-stu-id="d6c24-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="d6c24-122">在 DOM 中，XML 節點 (包括項目和屬性) 必須在 XML 文件的內容中建立。</span><span class="sxs-lookup"><span data-stu-id="d6c24-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="d6c24-123">此處為要在 DOM 中建立名稱項目之節點的片段：</span><span class="sxs-lookup"><span data-stu-id="d6c24-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="d6c24-124">如果您要跨多個文件使用同一個項目，您必須匯入跨這些文件的節點。</span><span class="sxs-lookup"><span data-stu-id="d6c24-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-125">可避免這層複雜度。</span><span class="sxs-lookup"><span data-stu-id="d6c24-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="d6c24-126">使用 LINQ to XML 時，您會使用<xref:System.Xml.Linq.XDocument>類別只有當您想要加入註解或處理指示文件的根層級。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="d6c24-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="d6c24-127">簡化的名稱和命名空間處理方式</span><span class="sxs-lookup"><span data-stu-id="d6c24-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="d6c24-128">名稱、命名空間和命名空間前置詞的處理通常是 XML 程式設計的複雜部分。</span><span class="sxs-lookup"><span data-stu-id="d6c24-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-129">名稱和命名空間，藉以簡化不必處理命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d6c24-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="d6c24-130">您也可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d6c24-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="d6c24-131">但是，如果您決定不明確控制命名空間前置詞，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]會在序列化期間指派命名空間前置詞，如果有必要，或使用預設命名空間，不會序列化。</span><span class="sxs-lookup"><span data-stu-id="d6c24-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="d6c24-132">如果使用預設的命名空間，在產生的文件中將不會有任何命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d6c24-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="d6c24-133">如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c24-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="d6c24-134">另一個 DOM 問題是，DOM 不會讓您變更節點的名稱，</span><span class="sxs-lookup"><span data-stu-id="d6c24-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="d6c24-135">而是必須建立新的節點，並將所有子節點複製到該節點中，因此會失去原始的節點識別。</span><span class="sxs-lookup"><span data-stu-id="d6c24-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-136">避免這個問題，方法是讓您設定<xref:System.Xml.Linq.XName>屬性節點上的。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="d6c24-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="d6c24-137">載入 XML 的靜態方法支援</span><span class="sxs-lookup"><span data-stu-id="d6c24-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-138">可讓您使用靜態方法，而非執行個體方法來載入 XML。</span><span class="sxs-lookup"><span data-stu-id="d6c24-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="d6c24-139">這會簡化載入和剖析的程序。</span><span class="sxs-lookup"><span data-stu-id="d6c24-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="d6c24-140">如需詳細資訊，請參閱[How to︰ 載入 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c24-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="d6c24-141">移除 DTD 建構函式的支援</span><span class="sxs-lookup"><span data-stu-id="d6c24-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-142"> 會移除實體和實體參考的支援，進一步簡化 XML 程式設計。</span><span class="sxs-lookup"><span data-stu-id="d6c24-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="d6c24-143">實體的管理很複雜，而且不常使用。</span><span class="sxs-lookup"><span data-stu-id="d6c24-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="d6c24-144">移除這些支援會增進效能並簡化程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="d6c24-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="d6c24-145">當[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]會填入樹狀結構，系統會展開所有 DTD 實體。</span><span class="sxs-lookup"><span data-stu-id="d6c24-145">When a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="d6c24-146">支援片段</span><span class="sxs-lookup"><span data-stu-id="d6c24-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-147">未提供的對等`XmlDocumentFragment`類別。</span><span class="sxs-lookup"><span data-stu-id="d6c24-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="d6c24-148">在許多情況下，不過，`XmlDocumentFragment`概念可處理的型別為查詢的結果<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XNode>，或<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>的</xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XNode></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="d6c24-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="d6c24-149">支援 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d6c24-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-150">提供支援<xref:System.Xml.XPath.XPathNavigator>中的擴充方法透過<xref:System.Xml.XPath?displayProperty=fullName>命名空間。</xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="d6c24-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="d6c24-151">如需詳細資訊，請參閱<xref:System.Xml.XPath.Extensions?displayProperty=fullName>。</xref:System.Xml.XPath.Extensions?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d6c24-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="d6c24-152">支援空白字元與縮排</span><span class="sxs-lookup"><span data-stu-id="d6c24-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-153">更輕鬆地處理泛空白字元比 DOM</span><span class="sxs-lookup"><span data-stu-id="d6c24-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="d6c24-154">常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="d6c24-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="d6c24-155">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="d6c24-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="d6c24-156">這是 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="d6c24-156">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="d6c24-157">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="d6c24-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="d6c24-158">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="d6c24-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="d6c24-159">在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，您就可以達到這個效果。</span><span class="sxs-lookup"><span data-stu-id="d6c24-159">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-160">儲存為泛空白字元<xref:System.Xml.Linq.XText>節點，而不需要的特定<xref:System.Xml.XmlNodeType>節點型別，dom 並未。</xref:System.Xml.XmlNodeType> </xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="d6c24-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="d6c24-161">支援附註</span><span class="sxs-lookup"><span data-stu-id="d6c24-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-162"> 項目支援一組可延伸的附註。</span><span class="sxs-lookup"><span data-stu-id="d6c24-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="d6c24-163">這在追蹤項目的其他資訊 (例如，結構描述資訊)、項目是否繫結至 UI 的相關資訊，或任何種類的應用程式專屬資訊時，相當實用。</span><span class="sxs-lookup"><span data-stu-id="d6c24-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="d6c24-164">如需詳細資訊，請參閱[LINQ to XML 註解](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5)。</span><span class="sxs-lookup"><span data-stu-id="d6c24-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="d6c24-165">支援結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="d6c24-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="d6c24-166">透過擴充方法中提供 XSD 驗證支援<xref:System.Xml.Schema?displayProperty=fullName>命名空間。</xref:System.Xml.Schema?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d6c24-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="d6c24-167">您可以驗證 XML 樹狀是以 XSD 編譯。</span><span class="sxs-lookup"><span data-stu-id="d6c24-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="d6c24-168">您可以利用 Post-Schema-Validation Infoset (PSVI) 填入 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="d6c24-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="d6c24-169">如需詳細資訊，請參閱[How to︰ 使用 XSD 驗證](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b)和<xref:System.Xml.Schema.Extensions>.</xref:System.Xml.Schema.Extensions></span><span class="sxs-lookup"><span data-stu-id="d6c24-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c24-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6c24-170">See Also</span></span>  
 [<span data-ttu-id="d6c24-171">使用者入門 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d6c24-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
