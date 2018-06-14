---
title: XML 項目常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 55d5d1410a65ea8c800bbd2b310907a6d6a61c61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605130"
---
# <a name="xml-element-literal-visual-basic"></a>XML 項目常值 (Visual Basic)

常值，表示<xref:System.Xml.Linq.XElement>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>組件  
  
-   `<`  
  
     必要。 開啟 開始項目標記。  
  
-   `name`  
  
     必要。 元素名稱。 格式為下列其中一項：  
  
    -   常值文字的項目名稱，表單`[ePrefix:]eName`，其中：  
  
        |組件|描述|  
        |---|---|  
        |`ePrefix`|選擇性。 XML 命名空間前置詞的項目。 必須是全域的 XML 命名空間定義與`Imports`檔案中，或在專案層級或本機的 XML 命名空間中這個項目或父項目所定義的陳述式。|  
        |`eName`|必要。 元素名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />內嵌運算式的形式`<%= eNameExp %>`。 型別`eNameExp`必須`String`或隱含轉換為型別<xref:System.Xml.Linq.XName>。|  
  
    -   內嵌運算式的形式`<%= nameExp %>`。 型別`nameExp`必須`String`或隱含地轉換成類型<xref:System.Xml.Linq.XName>。 項目的結尾標記中不允許內嵌的運算式。  
  
-   `attributeList`  
  
     選擇性。 常值中所宣告的屬性清單。  
  
     `attribute [ attribute ... ]`  
  
     每個`attribute`有一個下列語法：  
  
    -   屬性指派，表單`[aPrefix:]aName=aValue`，其中：  
  
        |組件|描述|  
        |---|---|  
        |`aPrefix`|選擇性。 屬性的 XML 命名空間前置詞。 必須是全域的 XML 命名空間定義與`Imports`陳述式或區域的 XML 命名空間中這個項目或父項目所定義。|  
        |`aName`|必要。 屬性的名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />內嵌運算式的形式`<%= aNameExp %>`。 型別`aNameExp`必須`String`或隱含轉換為型別<xref:System.Xml.Linq.XName>。|  
        |`aValue`|選擇性。 屬性的值。 格式為下列其中一項：<br /><br /> -常值文字，以引號括住。<br />內嵌運算式的形式`<%= aValueExp %>`。 不允許任何類型。|  
  
    -   內嵌運算式的形式`<%= aExp %>`。  
  
-   `/>`  
  
     選擇性。 表示項目是空的項目，不含內容。  
  
-   `>`  
  
     必要。 結束起始或空白項目標記。  
  
-   `elementContents`  
  
     選擇性。 項目的內容。  
  
     `content [ content ... ]`  
  
     每個`content`可以是下列其中之一：  
  
    -   常值文字。 中的所有空白字元`elementContents`太高，如果沒有任何常值文字。  
  
    -   內嵌運算式的形式`<%= contentExp %>`。  
  
    -   XML 元素常值。  
  
    -   XML 註解常值。 請參閱[XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。  
  
    -   XML 處理指示常值。 請參閱[XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。  
  
    -   XML CDATA 常值。 請參閱[XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)。  
  
-   `</[name]>`  
  
     選擇性。 代表項目的結尾標記。 選擇性`name`內嵌運算式的結果時，不允許參數。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XElement> 物件。  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 元素常值的語法來建立<xref:System.Xml.Linq.XElement>您的程式碼中的物件。  
  
> [!NOTE]
>  XML 常值可以跨越多行，而不使用行接續字元。 這項功能可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。  
  
 內嵌運算式的形式`<%= exp %>`可讓您將動態資訊加入至 XML 元素常值。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 Visual Basic 編譯器會將 XML 元素常值轉換成呼叫<xref:System.Xml.Linq.XElement.%23ctor%2A>建構函式，而且如果它是必要項，<xref:System.Xml.Linq.XAttribute.%23ctor%2A>建構函式。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 當您必須建立 XML 常值的項目和程式碼中多次相同的命名空間，XML 命名空間前置詞很有用。 您可以使用全域 XML 命名空間前置詞，您定義使用`Imports`陳述式或使用您定義的本機前置詞`xmlns:xmlPrefix="xmlNamespace"`屬性語法。 如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
 XML 命名空間之範圍規則，根據本機的前置詞的優先順序高於通用的前置詞。 不過，如果 XML 常值定義的 XML 命名空間，該命名空間不適用於內嵌的運算式中出現的運算式。 內嵌的運算式可以存取只有的全域 XML 命名空間。  
  
 Visual Basic 編譯器將轉換成產生的程式碼中的一個區域命名空間定義使用 XML 常值每個全域 XML 命名空間。 未使用的全域 XML 命名空間不會出現在產生的程式碼中。  
  
## <a name="example"></a>範例  
 下列範例會示範如何建立簡單的 XML 項目具有兩個巢狀的空項目。  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 此範例會顯示下列文字。 請注意，常值保留空白元素的結構。  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用內嵌的運算式來命名項目和建立屬性。  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後建立 XML 常值中使用的命名空間前置詞，並顯示項目的最終格式。  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 請注意編譯器，轉換成 XML 命名空間的前置詞定義的全域 XML 命名空間前置詞。 \<Ns:middle > 項目會重新定義的 XML 命名空間前置詞\<ns:inner1 > 項目。 不過， \<ns:inner2 > 元素會使用所定義的命名空間`Imports`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>  
 [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
