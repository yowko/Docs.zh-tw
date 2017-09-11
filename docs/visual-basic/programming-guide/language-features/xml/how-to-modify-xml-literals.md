---
title: "如何︰ 修改 XML 常值 (Visual Basic) |Microsoft 文件"
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
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c21ded9fdd8f49b469b9a712be304c0d4cabb8c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="f14d4-102">如何：修改 XML 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f14d4-102">How to: Modify XML Literals (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="f14d4-103">提供方便的方式，修改 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="f14d4-103"> provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="f14d4-104">您可以新增或刪除項目和屬性，您也可以使用新的 XML 項目取代現有的項目。</span><span class="sxs-lookup"><span data-stu-id="f14d4-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="f14d4-105">本主題提供如何修改現有的 XML 常值的數個範例。</span><span class="sxs-lookup"><span data-stu-id="f14d4-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="f14d4-106">若要修改 XML 常值的值</span><span class="sxs-lookup"><span data-stu-id="f14d4-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="f14d4-107">若要修改 XML 常值的值，取得 XML 常值和設定的參考`Value`屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="f14d4-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="f14d4-108">下列程式碼範例會更新所有的值\<價格 > 中的 XML 文件的項目。</span><span class="sxs-lookup"><span data-stu-id="f14d4-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     <span data-ttu-id="f14d4-109">[!code-vb[VbXmlSamples&#2;&4;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f14d4-109">[!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="f14d4-110">以下顯示範例來源 XML，並修改過這個程式碼範例的 XML。</span><span class="sxs-lookup"><span data-stu-id="f14d4-110">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
    >  <span data-ttu-id="f14d4-111">`Value`屬性參考集合中第一個 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="f14d4-111">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="f14d4-112">如果有多個集合中具有相同名稱的項目，設定`Value`屬性會影響的第一個元素的集合中。</span><span class="sxs-lookup"><span data-stu-id="f14d4-112">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="f14d4-113">若要將屬性加入至 XML 常值</span><span class="sxs-lookup"><span data-stu-id="f14d4-113">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="f14d4-114">若要將屬性加入至 XML 常值，先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="f14d4-114">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="f14d4-115">然後，您可以藉由新增新的 XML 屬性軸屬性加入屬性。</span><span class="sxs-lookup"><span data-stu-id="f14d4-115">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="f14d4-116">您也可以加入新<xref:System.Xml.Linq.XAttribute>物件 xml 常值使用<xref:System.Xml.Linq.XContainer.Add%2A>方法。</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="f14d4-116">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="f14d4-117">下列範例會示範這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="f14d4-117">The following example shows both options.</span></span>  
  
     <span data-ttu-id="f14d4-118">[!code-vb[VbXmlSamples&#2;&5;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f14d4-118">[!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="f14d4-119">以下顯示範例來源 XML，並修改過這個程式碼範例的 XML。</span><span class="sxs-lookup"><span data-stu-id="f14d4-119">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     <span data-ttu-id="f14d4-120">如需 XML 屬性軸屬性的詳細資訊，請參閱[XML 屬性軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)。</span><span class="sxs-lookup"><span data-stu-id="f14d4-120">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="f14d4-121">XML 常值中新增項目</span><span class="sxs-lookup"><span data-stu-id="f14d4-121">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="f14d4-122">若要加入 XML 常值中的項目，請先取得 XML 常值的參考。</span><span class="sxs-lookup"><span data-stu-id="f14d4-122">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="f14d4-123">您可以加入新<xref:System.Xml.Linq.XElement>物件做為最後一個子元素所使用的項目<xref:System.Xml.Linq.XContainer.Add%2A>方法。</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-123">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="f14d4-124">您可以新增一個<xref:System.Xml.Linq.XElement>物件做為第一個子元素使用<xref:System.Xml.Linq.XContainer.AddFirst%2A>方法。</xref:System.Xml.Linq.XContainer.AddFirst%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-124">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="f14d4-125">若要加入新項目在特定位置相對於其他子項目，請先取得相鄰的子元素的參考。</span><span class="sxs-lookup"><span data-stu-id="f14d4-125">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="f14d4-126">您可以加入新<xref:System.Xml.Linq.XElement>之前使用相鄰的子元素物件<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>方法。</xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-126">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="f14d4-127">您也可以加入新<xref:System.Xml.Linq.XElement>物件之後使用相鄰的子項目<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>方法。</xref:System.Xml.Linq.XNode.AddAfterSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-127">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="f14d4-128">下列範例會顯示每項技巧的範例。</span><span class="sxs-lookup"><span data-stu-id="f14d4-128">The following example shows examples of each of these techniques.</span></span>  
  
     <span data-ttu-id="f14d4-129">[!code-vb[VbXmlSamples&#2;&6;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f14d4-129">[!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="f14d4-130">以下顯示範例來源 XML，並修改過這個程式碼範例的 XML。</span><span class="sxs-lookup"><span data-stu-id="f14d4-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="f14d4-131">若要移除的項目或屬性從 XML 常值</span><span class="sxs-lookup"><span data-stu-id="f14d4-131">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="f14d4-132">若要從 XML 常值中移除項目或屬性，取得參考的項目或屬性和呼叫`Remove`方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f14d4-132">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     <span data-ttu-id="f14d4-133">[!code-vb[VbXmlSamples&#2;&7;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f14d4-133">[!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span></span>  
  
     <span data-ttu-id="f14d4-134">以下顯示範例來源 XML，並修改過這個程式碼範例的 XML。</span><span class="sxs-lookup"><span data-stu-id="f14d4-134">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
     <span data-ttu-id="f14d4-135">若要從 XML 常值中移除所有項目或屬性，取得 XML 常值的參考，並呼叫<xref:System.Xml.Linq.XElement.RemoveAll%2A>方法。</xref:System.Xml.Linq.XElement.RemoveAll%2A></span><span class="sxs-lookup"><span data-stu-id="f14d4-135">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="f14d4-136">若要修改 XML 常值</span><span class="sxs-lookup"><span data-stu-id="f14d4-136">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="f14d4-137">若要變更的 XML 項目名稱，請先取得項目的參考。</span><span class="sxs-lookup"><span data-stu-id="f14d4-137">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="f14d4-138">然後您可以建立新<xref:System.Xml.Linq.XElement>有新的名稱，並傳遞新物件<xref:System.Xml.Linq.XElement>物件傳遞給<xref:System.Xml.Linq.XNode.ReplaceWith%2A>現有方法<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode.ReplaceWith%2A> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-138">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="f14d4-139">如果您要取代的項目具有必須保留的子元素，來設定新值<xref:System.Xml.Linq.XElement>物件傳遞給<xref:System.Xml.Linq.XContainer.Nodes%2A>現有項目的屬性。</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f14d4-139">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="f14d4-140">這會將新項目的值為現有項目的內部 xml。</span><span class="sxs-lookup"><span data-stu-id="f14d4-140">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="f14d4-141">否則，您可以設定新的項目值`Value`現有項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="f14d4-141">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="f14d4-142">下列程式碼範例會取代所有\<描述 > 的項目\<抽象 > 項目。</span><span class="sxs-lookup"><span data-stu-id="f14d4-142">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="f14d4-143">內容的\<描述 > 項目會保留在新\<抽象 > 所使用的項目<xref:System.Xml.Linq.XContainer.Nodes%2A>屬性\<描述 ><xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Nodes%2A></span><span class="sxs-lookup"><span data-stu-id="f14d4-143">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="f14d4-144">[!code-vb[VbXmlSamples&#2;&8;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f14d4-144">[!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span></span>  
  
     <span data-ttu-id="f14d4-145">以下顯示範例來源 XML，並修改過這個程式碼範例的 XML。</span><span class="sxs-lookup"><span data-stu-id="f14d4-145">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
  
    Modified XML:  
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
  
## <a name="see-also"></a><span data-ttu-id="f14d4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f14d4-146">See Also</span></span>  
 <span data-ttu-id="f14d4-147">[在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f14d4-147">[Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="f14d4-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="f14d4-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="f14d4-149"> [如何︰ 從檔案、 字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="f14d4-149"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="f14d4-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="f14d4-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="f14d4-151"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="f14d4-151"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
