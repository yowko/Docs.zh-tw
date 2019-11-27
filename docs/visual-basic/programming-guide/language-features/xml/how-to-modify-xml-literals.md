---
title: 如何：修改 XML 常值
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 99ec35addcb9fc8d886c9151cde87227b5113eb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330850"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="cd0cc-102">如何：修改 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0cc-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="cd0cc-103">Visual Basic 提供便利的方式來修改 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="cd0cc-104">您可以新增或刪除專案和屬性，也可以使用新的 XML 元素來取代現有的專案。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="cd0cc-105">本主題提供數個範例，說明如何修改現有的 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="cd0cc-106">修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="cd0cc-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="cd0cc-107">若要修改 XML 常值的值，請取得 XML 常值的參考，並將 `Value` 屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="cd0cc-108">下列程式碼範例會更新 XML 檔中所有 \<Price > 元素的值。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="cd0cc-109">以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="cd0cc-110">來源 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-110">Source XML:</span></span>

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

    <span data-ttu-id="cd0cc-111">修改過的 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-111">Modified XML:</span></span>

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
    > <span data-ttu-id="cd0cc-112">`Value` 屬性指的是集合中的第一個 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="cd0cc-113">如果集合中有一個以上的專案具有相同的名稱，則設定 `Value` 屬性只會影響集合中的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="cd0cc-114">若要將屬性加入至 XML 常值</span><span class="sxs-lookup"><span data-stu-id="cd0cc-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="cd0cc-115">若要將屬性加入至 XML 常值，請先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="cd0cc-116">然後，您可以加入新的 XML 屬性軸屬性來新增屬性。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="cd0cc-117">您也可以使用 <xref:System.Xml.Linq.XContainer.Add%2A> 方法，將新的 <xref:System.Xml.Linq.XAttribute> 物件加入至 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="cd0cc-118">下列範例會顯示這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="cd0cc-119">以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="cd0cc-120">來源 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-120">Source XML:</span></span>

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

    <span data-ttu-id="cd0cc-121">修改過的 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-121">Modified XML:</span></span>

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

    <span data-ttu-id="cd0cc-122">如需 XML 屬性軸屬性的詳細資訊，請參閱[Xml 屬性軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="cd0cc-123">若要將元素加入至 XML 常值</span><span class="sxs-lookup"><span data-stu-id="cd0cc-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="cd0cc-124">若要將元素加入至 XML 常值，請先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="cd0cc-125">接著，您可以使用 <xref:System.Xml.Linq.XContainer.Add%2A> 方法，將新的 <xref:System.Xml.Linq.XElement> 物件當做專案的最後一個子項目加入。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="cd0cc-126">您可以使用 <xref:System.Xml.Linq.XContainer.AddFirst%2A> 方法，加入新的 <xref:System.Xml.Linq.XElement> 物件做為第一個子項目。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="cd0cc-127">若要在相對於其他子項目的特定位置加入新專案，請先取得相鄰子項目的參考。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="cd0cc-128">接著，您可以使用 <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> 方法，在相鄰子項目之前加入新的 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="cd0cc-129">您也可以使用 <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> 方法，在連續的子項目後面加入新的 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="cd0cc-130">下列範例顯示每個技術的範例。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="cd0cc-131">以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="cd0cc-132">來源 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-132">Source XML:</span></span>

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

    <span data-ttu-id="cd0cc-133">修改過的 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-133">Modified XML:</span></span>

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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="cd0cc-134">若要從 XML 常值中移除元素或屬性</span><span class="sxs-lookup"><span data-stu-id="cd0cc-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="cd0cc-135">若要從 XML 常值中移除元素或屬性，請取得元素或屬性的參考，並呼叫 `Remove` 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="cd0cc-136">以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="cd0cc-137">來源 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-137">Source XML:</span></span>

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

    <span data-ttu-id="cd0cc-138">修改過的 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-138">Modified XML:</span></span>

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

    <span data-ttu-id="cd0cc-139">若要從 XML 常值中移除所有元素或屬性，請取得 XML 常值的參考，並呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="cd0cc-140">修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="cd0cc-140">To modify an XML literal</span></span>

1. <span data-ttu-id="cd0cc-141">若要變更 XML 元素的名稱，請先取得元素的參考。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="cd0cc-142">接著，您可以建立新的 <xref:System.Xml.Linq.XElement> 物件，其中包含新的名稱，並將新的 <xref:System.Xml.Linq.XElement> 物件傳遞至現有 <xref:System.Xml.Linq.XElement> 物件的 <xref:System.Xml.Linq.XNode.ReplaceWith%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="cd0cc-143">如果您要取代的元素具有必須保留的子項目，請將新 <xref:System.Xml.Linq.XElement> 物件的值設定為現有專案的 <xref:System.Xml.Linq.XContainer.Nodes%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="cd0cc-144">這會將新元素的值設定為現有專案的內部 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="cd0cc-145">否則，您可以將新元素的值設定為現有元素的 `Value` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="cd0cc-146">下列程式碼範例會以 \<抽象 > 專案取代所有 \<描述 > 元素。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="cd0cc-147">\<描述 > 元素的內容會使用 <xref:System.Xml.Linq.XContainer.Nodes%2A> \<物件 > 描述的 <xref:System.Xml.Linq.XElement> 屬性，保留在新的 \<Abstract > 專案中。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="cd0cc-148">以下顯示此程式碼範例中的範例來源 XML 和修改過的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd0cc-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="cd0cc-149">來源 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-149">Source XML:</span></span>

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

    <span data-ttu-id="cd0cc-150">修改過的 XML：</span><span class="sxs-lookup"><span data-stu-id="cd0cc-150">Modified XML:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd0cc-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd0cc-151">See also</span></span>

- [<span data-ttu-id="cd0cc-152">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="cd0cc-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="cd0cc-153">XML</span><span class="sxs-lookup"><span data-stu-id="cd0cc-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="cd0cc-154">如何：從檔案、字串或資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="cd0cc-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="cd0cc-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="cd0cc-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="cd0cc-156">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="cd0cc-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
