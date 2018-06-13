---
title: 轉換中的結果樹狀片段
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c64baef3037cdb7b45ede3febacdbc1e76304c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574695"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="380ca-102">轉換中的結果樹狀片段</span><span class="sxs-lookup"><span data-stu-id="380ca-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="380ca-103"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="380ca-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="380ca-104">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="380ca-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="380ca-105">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="380ca-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="380ca-106">結果樹狀片段又稱為結果樹狀片段，其實就是指一種特殊型別的節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="380ca-107">您可以於其上進行任何可以在節點上進行的函式。</span><span class="sxs-lookup"><span data-stu-id="380ca-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="380ca-108">或者，您也可以使用 `node-set()` 函式將 result tree fragment 轉換成節點集，然後在任何可使用節點集的地方使用。</span><span class="sxs-lookup"><span data-stu-id="380ca-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="380ca-109">result tree fragment 是在樣式表中以特定方式使用 `<xsl:variable>` 或 `<xsl:param>` 項目所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="380ca-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="380ca-110">`variable` 和 `parameter` 項目的語法如下：</span><span class="sxs-lookup"><span data-stu-id="380ca-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="380ca-111">對於 `parameter` 項目，其值可透過數種方式指派給限定名稱 (`Qname`)。</span><span class="sxs-lookup"><span data-stu-id="380ca-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="380ca-112">您可以在 `select` 屬性中傳回 XML 路徑語言 (XPath) 運算式的內容，或者為其指派範本主體的內容，以將預設值指派給參數。</span><span class="sxs-lookup"><span data-stu-id="380ca-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="380ca-113">對 `variable` 項目而言，其值也可以透過數種方式來指派。</span><span class="sxs-lookup"><span data-stu-id="380ca-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="380ca-114">您可以在 `select` 屬性中傳回 XPath 運算式的內容，或為其指派範本主體的內容，以指派此值。</span><span class="sxs-lookup"><span data-stu-id="380ca-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="380ca-115">對於 `parameter` 與 `variable` 這兩個項目，若由 XPath 運算式指派其值，則會傳回四種基本 XPath 型別其中之一：布林值、數字、字串或節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="380ca-116">當值是由非空白的範本主體提供時，將傳回非 XPath 的資料型別，而它即是結果樹狀結構片段。</span><span class="sxs-lookup"><span data-stu-id="380ca-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="380ca-117">只有在變數繫結於結果樹狀結構片段而非四種基本 XPath 資料型別的其中一種時，XPath 查詢才會傳回非四種 XPath 物件型別的任何一種。</span><span class="sxs-lookup"><span data-stu-id="380ca-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="380ca-118">結果樹狀片段及其行為在全球資訊網協會 (W3C) 規格 (www.w3.org/XSLT) 中的 11.1 節＜結果樹狀片段＞至 11.6 節＜將參數傳遞至範本＞(英文) 中有所討論。</span><span class="sxs-lookup"><span data-stu-id="380ca-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="380ca-119">同時，第 1 節＜簡介＞(英文) 也討論了範本如何包含來自傳回或建立結果樹狀結構片段之 XSLT 命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="380ca-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="380ca-120">在概念上，結果樹狀結構片段的行為類似僅有單一根節點的節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="380ca-121">但是，所傳回的其他節點都是子節點。</span><span class="sxs-lookup"><span data-stu-id="380ca-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="380ca-122">若要以程式方式檢視子節點，請使用 `<xsl:copy-of>` 項目，將 result tree fragment 複製到結果樹狀結構上。</span><span class="sxs-lookup"><span data-stu-id="380ca-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="380ca-123">完成複製後，所有的子節點也會依序複製到結果樹狀結構上。</span><span class="sxs-lookup"><span data-stu-id="380ca-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="380ca-124">必須使用 `copy` 或 `copy-of`，result tree fragment 才會成為結果樹狀結構或轉換輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="380ca-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="380ca-125">若要反覆查看 result tree fragment 的傳回節點，便會使用 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="380ca-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="380ca-126">下列程式碼範例將說明，如何透過包含 XML 的參數 `fragment` 呼叫函式，以便在樣式表中建立 result tree fragment。</span><span class="sxs-lookup"><span data-stu-id="380ca-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:var name="fragment">  
        <node1>  
            <node2/>  
        </node1>  
    <xsl:var>  
  
  <msxsl:script language="C#" implements-prefix="user">  
    function NodeFragment(XPathNavigator nav)  
    {  
      if (nav.HasSelection == false)  
        XPathNavigator.MoveToNext();  
      return;  
    }  
  </msxsl:script>  
  
    <xsl:template match="/">  
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="380ca-127">以下將以 RTF 格式說明另一個變數範例，由於是 RTF，因此也是結果樹狀結構片段的型別之一，最後並未轉換成節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="380ca-128">它會傳遞至指令碼函式，而 <xref:System.Xml.XPath.XPathNavigator> 將用來導覽節點。</span><span class="sxs-lookup"><span data-stu-id="380ca-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNavigator nav)  
    {  
        bool b = nav.MoveToFirstChild();  
        if (b)  
            return nav.Value;  
        else  
            return "Does not exist";  
    }  
  
]]>  
  
</msxsl:script>  
  
<xsl:template match="/">  
    <first_book>  
        <xsl:value-of select="user:func($node-fragment)"/>  
    </first_book>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="380ca-129">使用這個樣式表轉換 XML 的結果會顯示在下列輸出中。</span><span class="sxs-lookup"><span data-stu-id="380ca-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="380ca-130">輸出</span><span class="sxs-lookup"><span data-stu-id="380ca-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="380ca-131">如上所述，`node-set` 函式讓您可以將 result tree fragment 轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="380ca-132">產生的節點集永遠包含單一節點，且為樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="380ca-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="380ca-133">如果您將 result tree fragment 轉換為節點集，即可將其用於一般節點集所使用之處，例如 for-each 陳述式或 `select` 屬性值之中。</span><span class="sxs-lookup"><span data-stu-id="380ca-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="380ca-134">下列程式行顯示，片段被轉換為節點集以及當做節點集使用：</span><span class="sxs-lookup"><span data-stu-id="380ca-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="380ca-135">當片段被轉換為節點集時，您就無法再使用 <xref:System.Xml.XPath.XPathNavigator> 加以導覽。</span><span class="sxs-lookup"><span data-stu-id="380ca-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="380ca-136">如果是節點集，請改用 <xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="380ca-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="380ca-137">下列範例中，`$var` 是樣式表內節點樹狀結構的變數。</span><span class="sxs-lookup"><span data-stu-id="380ca-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="380ca-138">for-each 陳述式和 `node-set` 函式結合，可讓使用者將這個樹狀結構當做節點集反覆查看。</span><span class="sxs-lookup"><span data-stu-id="380ca-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:variable name="states">  
        <node1>AL</node1>  
        <node1>CA</node1>  
        <node1>CO</node1>  
        <node1>WA</node1>  
    </xsl:variable>  
  
    <xsl:template match="/">  
            <xsl:for-each select="msxsl:node-set($states)"/>   
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="380ca-139">以下是另一個使用 RTF 格式的變數範例，由於是 RTF，因此屬於結果樹狀結構片段的型別，在作為 XPathNodeIterator 傳遞至指令碼函式之前，被轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="380ca-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNodeIterator it)  
    {  
        it.MoveNext();   
        return it.Current.Value;   
        //it.Current returns XPathNavigator positioned on the current node  
    }  
  
]]>  
  
</msxsl:script>  
<xsl:template match="/">  
    <books>  
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>  
    </books>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="380ca-140">以下是使用此樣式表轉換 XML 的結果：</span><span class="sxs-lookup"><span data-stu-id="380ca-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="380ca-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="380ca-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="380ca-142">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="380ca-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="380ca-143">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="380ca-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
