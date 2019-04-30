---
title: HOW TO：修改 XML 常值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 003715b04f3a5c0fb41e846beb189f117378ea58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053024"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="033b4-102">HOW TO：修改 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="033b4-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="033b4-103">Visual Basic 提供便利的方式來修改 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="033b4-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="033b4-104">您可以新增或刪除項目和屬性，您也可以使用新的 XML 項目取代現有的項目。</span><span class="sxs-lookup"><span data-stu-id="033b4-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="033b4-105">本主題提供如何修改現有的 XML 常值的數個範例。</span><span class="sxs-lookup"><span data-stu-id="033b4-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="033b4-106">若要修改 XML 常值的值</span><span class="sxs-lookup"><span data-stu-id="033b4-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="033b4-107">若要修改 XML 常值的值，取得 XML 常值和設定的參考`Value`屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="033b4-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="033b4-108">下列程式碼範例會更新所有的值\<價格 > 在 XML 文件中的項目。</span><span class="sxs-lookup"><span data-stu-id="033b4-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="033b4-109">下列示範範例來源 XML，並修改此程式碼範例中的 XML。</span><span class="sxs-lookup"><span data-stu-id="033b4-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="033b4-110">來源 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-110">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-111">修改過的 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-111">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>47.20</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>48.25</Price>
      </Book>
    </Catalog>
    ```

    > [!NOTE]
    > <span data-ttu-id="033b4-112">`Value`屬性參考集合中的第一個 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="033b4-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="033b4-113">如果在集合中具有相同名稱的多個項目，則設定`Value`屬性會影響僅在集合中的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="033b4-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="033b4-114">若要將屬性加入 XML 常值</span><span class="sxs-lookup"><span data-stu-id="033b4-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="033b4-115">若要加入 XML 常值中的屬性，請先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="033b4-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="033b4-116">然後，您就可以藉由新增新的 XML 屬性軸屬性加入屬性。</span><span class="sxs-lookup"><span data-stu-id="033b4-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="033b4-117">您也可以加入新<xref:System.Xml.Linq.XAttribute>要使用常值 XML 物件<xref:System.Xml.Linq.XContainer.Add%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="033b4-118">下列範例會示範這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="033b4-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="033b4-119">下列示範範例來源 XML，並修改此程式碼範例中的 XML。</span><span class="sxs-lookup"><span data-stu-id="033b4-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="033b4-120">來源 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-120">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-121">修改過的 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-121">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-122">如需有關 XML 屬性軸屬性的詳細資訊，請參閱[XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)。</span><span class="sxs-lookup"><span data-stu-id="033b4-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="033b4-123">XML 常值中新增項目</span><span class="sxs-lookup"><span data-stu-id="033b4-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="033b4-124">若要加入 XML 常值中的項目，請先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="033b4-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="033b4-125">然後您可以加入新<xref:System.Xml.Linq.XElement>物件做為最後一個子元素所使用之項目的<xref:System.Xml.Linq.XContainer.Add%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="033b4-126">您可以加入新<xref:System.Xml.Linq.XElement>物件所使用的第一個子元素<xref:System.Xml.Linq.XContainer.AddFirst%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="033b4-127">若要在特定位置相對於其他子元素中新增新的項目，請先取得相鄰的子元素的參考。</span><span class="sxs-lookup"><span data-stu-id="033b4-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="033b4-128">然後您可以加入新<xref:System.Xml.Linq.XElement>之前使用相鄰的子元素物件<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="033b4-129">您也可以加入新<xref:System.Xml.Linq.XElement>之後使用相鄰的子元素物件<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="033b4-130">下列範例顯示的每一個技巧的範例。</span><span class="sxs-lookup"><span data-stu-id="033b4-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="033b4-131">下列示範範例來源 XML，並修改此程式碼範例中的 XML。</span><span class="sxs-lookup"><span data-stu-id="033b4-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="033b4-132">來源 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-132">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-133">修改過的 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-133">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" >
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331">
        <Publisher>Microsoft Press</Publisher>
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <PublishDate>2005-2-14</PublishDate>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="033b4-134">若要移除 XML 常值中的項目或屬性</span><span class="sxs-lookup"><span data-stu-id="033b4-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="033b4-135">若要移除 XML 常值的元素或屬性，取得參考的項目或屬性和呼叫`Remove`方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="033b4-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="033b4-136">下列示範範例來源 XML，並修改此程式碼範例中的 XML。</span><span class="sxs-lookup"><span data-stu-id="033b4-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="033b4-137">來源 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-137">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book>
      <Book id="bk999"></Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-138">修改過的 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-138">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101" editorEmail="someone@example.com">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
      </Book>
      <Book id="bk000"></Book>
      <Book id="bk331" editorEmail="someone@example.com">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
      </Book></Catalog>
    ```

    <span data-ttu-id="033b4-139">若要移除 XML 常值的所有項目或屬性，取得 XML 常值的參考，並呼叫<xref:System.Xml.Linq.XElement.RemoveAll%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="033b4-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="033b4-140">若要修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="033b4-140">To modify an XML literal</span></span>

1. <span data-ttu-id="033b4-141">若要變更的 XML 項目名稱，請先取得項目的參考。</span><span class="sxs-lookup"><span data-stu-id="033b4-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="033b4-142">然後您可以建立新<xref:System.Xml.Linq.XElement>有新的名稱，並傳遞新的物件<xref:System.Xml.Linq.XElement>物件<xref:System.Xml.Linq.XNode.ReplaceWith%2A>方法的現有<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="033b4-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="033b4-143">如果您要取代的項目必須保留的子元素，來設定新值<xref:System.Xml.Linq.XElement>物件至<xref:System.Xml.Linq.XContainer.Nodes%2A>現有項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="033b4-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="033b4-144">這會將新的項目值的現有項目內部的 xml。</span><span class="sxs-lookup"><span data-stu-id="033b4-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="033b4-145">否則，您可以設定為新的項目值`Value`現有項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="033b4-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="033b4-146">下列程式碼範例會取代所有\<描述 > 項目\<抽象 > 項目。</span><span class="sxs-lookup"><span data-stu-id="033b4-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="033b4-147">內容\<描述 > 項目會保留在新\<抽象 > 所使用的項目<xref:System.Xml.Linq.XContainer.Nodes%2A>屬性\<描述 ><xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="033b4-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="033b4-148">下列示範範例來源 XML，並修改此程式碼範例中的 XML。</span><span class="sxs-lookup"><span data-stu-id="033b4-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="033b4-149">來源 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-149">Source XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <Price>44.95</Price>
        <Description>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Description>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <Price>45.95</Price>
        <Description>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Description>
      </Book>
    </Catalog>
    ```

    <span data-ttu-id="033b4-150">修改過的 XML:</span><span class="sxs-lookup"><span data-stu-id="033b4-150">Modified XML:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Catalog>
      <Book id="bk101">
        <Author>Garghentini, Davide</Author>
        <Title>XML Developer's Guide</Title>
        <MSRP>44.95</MSRP>    <Abstract>
          An in-depth look at creating applications
          with <technology>XML</technology>. For
          <audience>beginners</audience> or
          <audience>advanced</audience> developers.
        </Abstract>
      </Book>
      <Book id="bk331">
        <Author>Spencer, Phil</Author>
        <Title>Developing Applications with Visual Basic .NET</Title>
        <MSRP>45.95</MSRP>    <Abstract>
          Get the expert insights, practical code samples, and best
          practices you need to advance your expertise with
          <technology>Visual Basic .NET</technology>.
          Learn how to create faster, more reliable applications
          based on professional, pragmatic guidance by today's top
          <audience>developers</audience>.
        </Abstract>
      </Book>
    </Catalog>
    ```

## <a name="see-also"></a><span data-ttu-id="033b4-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="033b4-151">See also</span></span>

- [<span data-ttu-id="033b4-152">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="033b4-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="033b4-153">XML</span><span class="sxs-lookup"><span data-stu-id="033b4-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="033b4-154">如何：從檔案、 字串或 Stream 載入 XML</span><span class="sxs-lookup"><span data-stu-id="033b4-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="033b4-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="033b4-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="033b4-156">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="033b4-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
