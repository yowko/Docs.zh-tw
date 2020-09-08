---
title: LINQ to XML 比較DOM
description: LINQ to XML 與 DOM 之間有一些主要差異。 LINQ to XML 支援功能結構和 XML 常值，以更好的顯示其所建立之 XML 樹狀結構的結構。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552229"
---
# <a name="linq-to-xml-vs-dom"></a><span data-ttu-id="f17b2-104">LINQ to XML 比較DOM</span><span class="sxs-lookup"><span data-stu-id="f17b2-104">LINQ to XML vs. DOM</span></span>

<span data-ttu-id="f17b2-105">本文描述 LINQ to XML 和目前主流 XML 程式設計 API （W3C 檔物件模型 (DOM) 之間的一些主要差異。</span><span class="sxs-lookup"><span data-stu-id="f17b2-105">This article describes some key differences between LINQ to XML and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>

## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="f17b2-106">建立 XML 樹狀結構的新方式</span><span class="sxs-lookup"><span data-stu-id="f17b2-106">New ways to construct XML trees</span></span>

<span data-ttu-id="f17b2-107">在 W3C DOM 中，您可以從下往上建置 XML 樹狀；也就是說，您可以建立文件、建立項目，然後將項目加入到文件中。</span><span class="sxs-lookup"><span data-stu-id="f17b2-107">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>

<span data-ttu-id="f17b2-108">例如，下列範例會使用一般的方式，利用 Microsoft 的 DOM 執行來建立 XML 樹狀結構 <xref:System.Xml.XmlDocument> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-108">For example, the following example uses a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>.</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

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

<span data-ttu-id="f17b2-109">這種編碼樣式會隱藏 XML 樹狀結構的結構。</span><span class="sxs-lookup"><span data-stu-id="f17b2-109">This style of coding hides the structure of the XML tree.</span></span> <span data-ttu-id="f17b2-110">LINQ to XML 也支援另一種方法，也就是 *功能結構*，更適合用來顯示結構。</span><span class="sxs-lookup"><span data-stu-id="f17b2-110">LINQ to XML also supports an alternative approach, *functional construction*, that better shows the structure.</span></span> <span data-ttu-id="f17b2-111">這種方法可以使用和函式來完成 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-111">This approach can be done with the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors.</span></span> <span data-ttu-id="f17b2-112">在 Visual Basic 中，也可以使用 XML 常值來完成。</span><span class="sxs-lookup"><span data-stu-id="f17b2-112">In Visual Basic, it can also be done with XML literals.</span></span> <span data-ttu-id="f17b2-113">此範例示範如何使用功能結構來建立相同的 XML 樹狀結構：</span><span class="sxs-lookup"><span data-stu-id="f17b2-113">This example demonstrates construction of the same XML tree using functional construction:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),
            new XElement("phone", "425-555-0145",
                new XAttribute("Type", "Work")),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

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

<span data-ttu-id="f17b2-114">請注意，將要建構 XML 樹狀結構的程式碼縮排可顯示基礎 XML 的結構。</span><span class="sxs-lookup"><span data-stu-id="f17b2-114">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span> <span data-ttu-id="f17b2-115">Visual Basic 版本會使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="f17b2-115">The Visual Basic version uses XML literals.</span></span>

<span data-ttu-id="f17b2-116">如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。</span><span class="sxs-lookup"><span data-stu-id="f17b2-116">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="work-directly-with-xml-elements"></a><span data-ttu-id="f17b2-117">直接使用 XML 元素</span><span class="sxs-lookup"><span data-stu-id="f17b2-117">Work directly with XML elements</span></span>

<span data-ttu-id="f17b2-118">當您使用 XML 進行程式設計時，您的主要焦點通常是 XML 項目，也可能是屬性。</span><span class="sxs-lookup"><span data-stu-id="f17b2-118">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="f17b2-119">在 LINQ to XML 中，您可以直接使用 XML 元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="f17b2-119">In LINQ to XML, you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="f17b2-120">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="f17b2-120">For example, you can do the following:</span></span>

- <span data-ttu-id="f17b2-121">完全不使用文件物件來建立 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="f17b2-121">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="f17b2-122">當您必須使用 XML 樹狀結構的片段時，這可以簡化程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="f17b2-122">This simplifies programming when you have to work with fragments of XML trees.</span></span>
- <span data-ttu-id="f17b2-123">從 XML 檔案直接載入 `T:System.Xml.Linq.XElement` 物件。</span><span class="sxs-lookup"><span data-stu-id="f17b2-123">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>
- <span data-ttu-id="f17b2-124">將 `T:System.Xml.Linq.XElement` 物件序列化為檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="f17b2-124">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>

<span data-ttu-id="f17b2-125">將這個 XML 項目或屬性與 W3C DOM 相比較，後者中的 XML 文件會當做 XML 樹狀結構的邏輯容器使用。</span><span class="sxs-lookup"><span data-stu-id="f17b2-125">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="f17b2-126">在 DOM 中，XML 節點 (包括項目和屬性) 必須在 XML 文件的內容中建立。</span><span class="sxs-lookup"><span data-stu-id="f17b2-126">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="f17b2-127">以下是在 DOM 中建立 name 元素的程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="f17b2-127">Here is a fragment of code to create a name element in DOM:</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

<span data-ttu-id="f17b2-128">如果您要跨多個文件使用同一個項目，您必須匯入跨這些文件的節點。</span><span class="sxs-lookup"><span data-stu-id="f17b2-128">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> <span data-ttu-id="f17b2-129">LINQ to XML 可避免這層複雜度。</span><span class="sxs-lookup"><span data-stu-id="f17b2-129">LINQ to XML avoids this layer of complexity.</span></span>

<span data-ttu-id="f17b2-130">使用 LINQ to XML 時，您僅能在想要於文件根層級上加入註解或處理指示時，才能使用 <xref:System.Xml.Linq.XDocument> 類別。</span><span class="sxs-lookup"><span data-stu-id="f17b2-130">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>

## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="f17b2-131">簡化名稱和命名空間的處理</span><span class="sxs-lookup"><span data-stu-id="f17b2-131">Simplified handling of names and namespaces</span></span>

<span data-ttu-id="f17b2-132">名稱、命名空間和命名空間前置詞的處理通常是 XML 程式設計的複雜部分。</span><span class="sxs-lookup"><span data-stu-id="f17b2-132">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="f17b2-133">LINQ to XML 藉由消除處理命名空間前置詞的需求，來簡化名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="f17b2-133">LINQ to XML simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="f17b2-134">您也可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f17b2-134">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="f17b2-135">但是，如果您決定不明確控制命名空間前置詞，LINQ to XML 會在序列化期間指派命名空間前置詞（如果需要的話），否則會使用預設的命名空間進行序列化（如果不是的話）。</span><span class="sxs-lookup"><span data-stu-id="f17b2-135">But if you decide to not explicitly control namespace prefixes, LINQ to XML will assign namespace prefixes during serialization if they're required, or will serialize using default namespaces if they're not.</span></span> <span data-ttu-id="f17b2-136">如果使用預設的命名空間，在產生的文件中將不會有任何命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="f17b2-136">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="f17b2-137">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b2-137">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="f17b2-138">DOM 的另一個問題是，它不會讓您變更節點的名稱。</span><span class="sxs-lookup"><span data-stu-id="f17b2-138">Another problem with the DOM is that it doesn't let you change the name of a node.</span></span> <span data-ttu-id="f17b2-139">而是必須建立新的節點，並將所有子節點複製到該節點中，因此會失去原始的節點識別。</span><span class="sxs-lookup"><span data-stu-id="f17b2-139">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> <span data-ttu-id="f17b2-140">LINQ to XML 可讓您在節點上設定屬性，以避免這個問題 <xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-140">LINQ to XML avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>

## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="f17b2-141">載入 XML 的靜態方法支援</span><span class="sxs-lookup"><span data-stu-id="f17b2-141">Static method support for loading XML</span></span>

<span data-ttu-id="f17b2-142">LINQ to XML 可讓您使用靜態方法（而非實例方法）載入 XML。</span><span class="sxs-lookup"><span data-stu-id="f17b2-142">LINQ to XML lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="f17b2-143">這會簡化載入和剖析的程序。</span><span class="sxs-lookup"><span data-stu-id="f17b2-143">This simplifies loading and parsing.</span></span> <span data-ttu-id="f17b2-144">如需詳細資訊，請參閱 [如何從檔案載入 XML](load-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b2-144">For more information, see [How to load XML from a file](load-xml-file.md).</span></span>

## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="f17b2-145">移除 DTD 結構的支援</span><span class="sxs-lookup"><span data-stu-id="f17b2-145">Removal of support for DTD constructs</span></span>

<span data-ttu-id="f17b2-146">LINQ to XML 藉由移除實體和實體參考的支援，進一步簡化 XML 程式設計。</span><span class="sxs-lookup"><span data-stu-id="f17b2-146">LINQ to XML further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="f17b2-147">實體的管理很複雜，而且不常使用。</span><span class="sxs-lookup"><span data-stu-id="f17b2-147">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="f17b2-148">移除這些支援會增進效能並簡化程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="f17b2-148">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="f17b2-149">填入 LINQ to XML 的樹狀結構時，就會展開所有 DTD 實體。</span><span class="sxs-lookup"><span data-stu-id="f17b2-149">When a LINQ to XML tree is populated, all DTD entities are expanded.</span></span>

## <a name="support-for-fragments"></a><span data-ttu-id="f17b2-150">支援片段</span><span class="sxs-lookup"><span data-stu-id="f17b2-150">Support for fragments</span></span>

<span data-ttu-id="f17b2-151">LINQ to XML 不會提供類別的對等專案 `XmlDocumentFragment` 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-151">LINQ to XML doesn't provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="f17b2-152">不過，在許多情況下，此 `XmlDocumentFragment` 概念可以由類型為 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> 或的查詢結果來處理 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-152">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that's typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>

## <a name="support-for-xpathnavigator"></a><span data-ttu-id="f17b2-153">支援 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f17b2-153">Support for XPathNavigator</span></span>

<span data-ttu-id="f17b2-154">LINQ to XML <xref:System.Xml.XPath.XPathNavigator> 透過命名空間中的擴充方法提供支援 <xref:System.Xml.XPath?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-154">LINQ to XML provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f17b2-155">如需詳細資訊，請參閱<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f17b2-155">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="f17b2-156">空白字元和縮排的支援</span><span class="sxs-lookup"><span data-stu-id="f17b2-156">Support for white space and indentation</span></span>

<span data-ttu-id="f17b2-157">LINQ to XML 會比 DOM 更簡單地處理空白字元。</span><span class="sxs-lookup"><span data-stu-id="f17b2-157">LINQ to XML handles white space more simply than the DOM.</span></span>

<span data-ttu-id="f17b2-158">常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。</span><span class="sxs-lookup"><span data-stu-id="f17b2-158">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f17b2-159">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="f17b2-159">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f17b2-160">這是 LINQ to XML 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="f17b2-160">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="f17b2-161">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="f17b2-161">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f17b2-162">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="f17b2-162">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f17b2-163">在 LINQ to XML 中，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f17b2-163">In LINQ to XML, you can do this by:</span></span>

- <span data-ttu-id="f17b2-164">載入或剖析 XML 時保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="f17b2-164">Preserving white space when you load or parse the XML.</span></span>
- <span data-ttu-id="f17b2-165">當您序列化 XML 時停用格式。</span><span class="sxs-lookup"><span data-stu-id="f17b2-165">Disabling formatting when you serialize the XML.</span></span>

<span data-ttu-id="f17b2-166">LINQ to XML 會將空白字元儲存為 <xref:System.Xml.Linq.XText> 節點，而不是使用特製化的 <xref:System.Xml.XmlNodeType.Whitespace> 節點類型，如同 DOM 一樣。</span><span class="sxs-lookup"><span data-stu-id="f17b2-166">LINQ to XML stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>

## <a name="support-for-annotations"></a><span data-ttu-id="f17b2-167">支援注釋</span><span class="sxs-lookup"><span data-stu-id="f17b2-167">Support for annotations</span></span>

<span data-ttu-id="f17b2-168">LINQ to XML 元素支援一組可擴充的注釋。</span><span class="sxs-lookup"><span data-stu-id="f17b2-168">LINQ to XML elements support an extensible set of annotations.</span></span> <span data-ttu-id="f17b2-169">這在追蹤項目的其他資訊 (例如，結構描述資訊)、項目是否繫結至 UI 的相關資訊，或任何種類的應用程式專屬資訊時，相當實用。</span><span class="sxs-lookup"><span data-stu-id="f17b2-169">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="f17b2-170">如需詳細資訊，請參閱 [LINQ to XML 附注](linq-xml-annotations.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b2-170">For more information, see [LINQ to XML annotations](linq-xml-annotations.md).</span></span>

## <a name="support-for-schema-information"></a><span data-ttu-id="f17b2-171">架構資訊的支援</span><span class="sxs-lookup"><span data-stu-id="f17b2-171">Support for schema information</span></span>

<span data-ttu-id="f17b2-172">LINQ to XML 透過命名空間中的擴充方法，提供 XSD 驗證的支援 <xref:System.Xml.Schema?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-172">LINQ to XML provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f17b2-173">您可以驗證 XML 樹狀是以 XSD 編譯。</span><span class="sxs-lookup"><span data-stu-id="f17b2-173">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="f17b2-174">您可以利用 Post-Schema-Validation Infoset (PSVI) 填入 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="f17b2-174">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="f17b2-175">如需詳細資訊，請參閱 [如何使用 XSD 和進行驗證](validate-xsd.md) <xref:System.Xml.Schema.Extensions> 。</span><span class="sxs-lookup"><span data-stu-id="f17b2-175">For more information, see [How to validate using XSD](validate-xsd.md) and <xref:System.Xml.Schema.Extensions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f17b2-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f17b2-176">See also</span></span>

- [<span data-ttu-id="f17b2-177">LINQ to XML 總覽</span><span class="sxs-lookup"><span data-stu-id="f17b2-177">LINQ to XML overview</span></span>](linq-xml-overview.md)
