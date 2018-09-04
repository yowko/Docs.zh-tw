---
title: 轉換中的結果樹狀片段
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca6871886a64c864451eb3e2f6f4843e0150123b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553016"
---
# <a name="result-tree-fragment-in-transformations"></a>轉換中的結果樹狀片段

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](migrating-from-the-xsltransform-class.md)。

 結果樹狀片段又稱為結果樹狀片段，其實就是指一種特殊型別的節點集。 您可以於其上進行任何可以在節點上進行的函式。 或者，您也可以使用 `node-set()` 函式將 result tree fragment 轉換成節點集，然後在任何可使用節點集的地方使用。

 result tree fragment 是在樣式表中以特定方式使用 `<xsl:variable>` 或 `<xsl:param>` 項目所產生的結果。 `variable` 和 `parameter` 項目的語法如下：

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

對於 `parameter` 項目，其值可透過數種方式指派給限定名稱 (`Qname`)。 您可以在 `select` 屬性中傳回 XML 路徑語言 (XPath) 運算式的內容，或者為其指派範本主體的內容，以將預設值指派給參數。

對 `variable` 項目而言，其值也可以透過數種方式來指派。 您可以在 `select` 屬性中傳回 XPath 運算式的內容，或為其指派範本主體的內容，以指派此值。

對於 `parameter` 與 `variable` 這兩個項目，若由 XPath 運算式指派其值，則會傳回四種基本 XPath 型別其中之一：布林值、數字、字串或節點集。 當值是由非空白的範本主體提供時，將傳回非 XPath 的資料型別，而它即是結果樹狀結構片段。

只有在變數繫結程序於結果樹狀片段而非四種基本 XPath 資料型別的其中一種時，XPath 查詢才會傳回非四種 XPath 物件型別的任何一種。 結果樹狀片段及其行為在[全球資訊網協會 (W3C) 規格](https://www.w3.org/TR/xslt-10/)中的 [11.1 節＜結果樹狀片段＞](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments)至 [11.6 節＜將參數傳遞至範本＞](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates)\(英文\) 中有所討論。 此外，[第 1 節＜簡介＞](https://www.w3.org/TR/xslt-10/#section-Introduction)\(英文) 也討論了範本如何包含來自傳回或建立結果樹狀片段之 XSLT 命名空間的項目。

在概念上，結果樹狀片段的行為類似僅有單一根節點的節點集。 但是，所傳回的其他節點都是子節點。 若要以程式方式檢視子節點，請使用 `<xsl:copy-of>` 項目，將 result tree fragment 複製到結果樹狀結構上。 完成複製後，所有的子節點也會依序複製到結果樹狀結構上。 必須使用 `copy` 或 `copy-of`，result tree fragment 才會成為結果樹狀結構或轉換輸出的一部分。

若要反覆查看 result tree fragment 的傳回節點，便會使用 <xref:System.Xml.XPath.XPathNavigator>。 下列程式碼範例將說明，如何透過包含 XML 的參數 `fragment` 呼叫函式，以便在樣式表中建立 result tree fragment。

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

以下將以 RTF 格式說明另一個變數範例，由於是 RTF，因此也是結果樹狀結構片段的型別之一，最後並未轉換成節點集。 它會傳遞至指令碼函式，而 <xref:System.Xml.XPath.XPathNavigator> 將用來導覽節點。

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

使用這個樣式表轉換 XML 的結果會顯示在下列輸出中。

## <a name="output"></a>輸出

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

如上所述，`node-set` 函式讓您可以將 result tree fragment 轉換為節點集。 產生的節點集永遠包含單一節點，且為樹狀結構的根節點。 如果您將 result tree fragment 轉換為節點集，即可將其用於一般節點集所使用之處，例如 for-each 陳述式或 `select` 屬性值之中。 下列程式行顯示，片段被轉換為節點集以及當做節點集使用：

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

當片段被轉換為節點集時，您就無法再使用 <xref:System.Xml.XPath.XPathNavigator> 加以導覽。 如果是節點集，請改用 <xref:System.Xml.XPath.XPathNodeIterator>。

下列範例中，`$var` 是樣式表內節點樹狀結構的變數。 for-each 陳述式和 `node-set` 函式結合，可讓使用者將這個樹狀結構當做節點集反覆查看。

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

以下是另一個使用 RTF 格式的變數範例，由於是 RTF，因此屬於結果樹狀結構片段的型別，在作為 XPathNodeIterator 傳遞至指令碼函式之前，被轉換為節點集。

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

以下是使用此樣式表轉換 XML 的結果：

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>請參閱

<xref:System.Xml.XPath.XPathNodeIterator>  
<xref:System.Xml.XPath.XPathNodeIterator>  
[使用 XslTransform 類別進行 XSLT 轉換](xslt-transformations-with-the-xsltransform-class.md)  
[XslTransform 類別實作 XSLT 處理器](xsltransform-class-implements-the-xslt-processor.md)  
