---
title: "XML 項目常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c77a1ec3621d056a814b298cd5ee6b8c44c52ec2
ms.lasthandoff: 03/13/2017

---
# <a name="xml-element-literal-visual-basic"></a>XML 項目常值 (Visual Basic)
常值，表示<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>語法  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>組件  
  
-   `<`  
  
     必要項。 開啟起始項目標記。  
  
-   `name`  
  
     必要項。 元素名稱。 格式為下列其中一項︰  
  
    -   常值文字的項目名稱，表單的 [`ePrefix``:`]`eName`，其中︰  
  
        |組件|說明|  
        |---|---|  
        |`ePrefix`|選擇項。 項目的 XML 命名空間前置詞。 必須是全域的 XML 命名空間定義的`Imports`陳述式在檔案或專案層級中，或本機的 XML 命名空間定義於這個項目或父項目。|  
        |`eName`|必要項。 元素名稱。 格式為下列其中一項︰<br /><br /> -常值文字。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />內嵌運算式格式`<%=`e`NameExp` `%>`。 型別`eNameExp`必須`String`或可隱含轉換至<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>型別|  
  
    -   內嵌運算式格式`<%=` `nameExp` `%>`。 型別`nameExp`必須`String`或隱含地轉換成<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>類型 項目的結尾標記中不允許內嵌的運算式。  
  
-   `attributeList`  
  
     選擇項。 常值中宣告之屬性清單。  
  
     `attribute [ attribute ... ]`  
  
     每個`attribute`有下列語法︰  
  
    -   屬性指派，表單的 [`aPrefix``:`]`aName``=``aValue`，其中︰  
  
        |組件|說明|  
        |---|---|  
        |`aPrefix`|選擇項。 屬性的 XML 命名空間前置詞。 必須是全域的 XML 命名空間定義的`Imports`陳述式或區域的 XML 命名空間定義於這個項目或父項目。|  
        |`aName`|必要項。 屬性的名稱。 格式為下列其中一項︰<br /><br /> -常值文字。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />內嵌運算式格式`<%=` `aNameExp` `%>`。 型別`aNameExp`必須`String`或可隱含轉換至<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>型別|  
        |`aValue`|選擇項。 屬性的值。 格式為下列其中一項︰<br /><br /> -常值文字，以引號括住。<br />內嵌運算式格式`<%=` `aValueExp` `%>`。 允許任何型別。|  
  
    -   內嵌運算式格式`<%=` `aExp` `%>`。  
  
-   `/>`  
  
     選擇項。 表示的項目是空的項目，不含內容。  
  
-   `>`  
  
     必要項。 結束開始或空白項目標記。  
  
-   `elementContents`  
  
     選擇項。 項目的內容。  
  
     `content [ content ... ]`  
  
     每個`content`可以是下列其中之一︰  
  
    -   常值文字。 中的所有泛空白字元`elementContents`太高，如果沒有任何常值文字。  
  
    -   內嵌運算式格式`<%=` `contentExp` `%>`。  
  
    -   XML 項目常值。  
  
    -   XML 註解常值。 請參閱[XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。  
  
    -   XML 處理指示常值。 請參閱[XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。  
  
    -   XML CDATA 常值。 請參閱[XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)。  
  
-   `</`[`name`]`>`  
  
     選擇項。 表示項目的結尾標記。 選擇性`name`參數不允許內嵌的運算式的結果時。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 項目常值語法來建立<xref:System.Xml.Linq.XElement>您的程式碼中的物件。</xref:System.Xml.Linq.XElement>  
  
> [!NOTE]
>  XML 常值可以跨越多行程式碼，而不需使用行接續字元。 這項功能可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 內嵌運算式形式的`<%=` `exp` `%>`可讓您將動態資訊加入至 XML 項目常值。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 項目常值轉換成呼叫<xref:System.Xml.Linq.XElement.%23ctor%2A>建構函式，而且如果它是必要項目，<xref:System.Xml.Linq.XAttribute.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A>  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 當您必須建立 XML 常值的項目和程式碼中多次相同的命名空間，XML 命名空間前置詞很有用。 您可以使用全域 XML 命名空間前置詞，以您定義使用`Imports`陳述式或使用您定義的本機首碼`xmlns:``xmlPrefix`="`xmlNamespace`"屬性語法。 如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
 XML 命名空間的範圍設定規則，根據本機前置詞的優先順序高於全域首碼。 不過，如果 XML 常值定義的 XML 命名空間，該命名空間不適用於內嵌的運算式中出現的運算式。 內嵌的運算式可以存取只有通用的 XML 命名空間。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器將會使用 XML 常值至產生的程式碼中的一個區域命名空間定義每個全域 XML 命名空間。 產生的程式碼中看不到未使用的全域 XML 命名空間。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立簡單的 XML 項目具有兩個巢狀的空項目。  
  
 [!code-vb[VbXMLSamples #&20;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 此範例會顯示下列文字。 請注意，常值保留空白項目結構。  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用內嵌的運算式來命名項目和建立屬性。  
  
 [!code-vb[VbXMLSamples #&21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 此程式碼顯示下列文字：  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後建立 XML 常值中使用的命名空間前置詞，並顯示項目的最終格式。  
  
 [!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 此程式碼顯示下列文字：  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 請注意，編譯器的轉換成 XML 命名空間的前置詞定義全域 XML 命名空間的前置詞。 \<Ns:middle > 項目重新定義的 XML 命名空間前置詞\<ns:inner1 > 項目。 不過， \<ns:inner2 > 項目會使用所定義的命名空間`Imports`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>   
 [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
