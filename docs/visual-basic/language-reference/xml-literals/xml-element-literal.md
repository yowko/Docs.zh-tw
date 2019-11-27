---
title: XML 元素常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347033"
---
# <a name="xml-element-literal-visual-basic"></a>XML 項目常值 (Visual Basic)

表示 <xref:System.Xml.Linq.XElement> 物件的常值。

## <a name="syntax"></a>語法

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>組件

- `<`

  必要。 開啟起始元素標記。

- `name`

  必要。 元素名稱。 格式為下列其中一項：

  - 元素名稱的常值文字，格式為 `[ePrefix:]eName`，其中：

    |組件|描述|
    |---|---|
    |`ePrefix`|選擇性。 元素的 XML 命名空間前置詞。 必須是以檔案中的 `Imports` 語句或專案層級定義的全域 XML 命名空間，或是在此元素或父元素中定義的本機 XML 命名空間。|
    |`eName`|必要。 元素名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱宣告[的 XML 元素和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />-表單 `<%= eNameExp %>`的內嵌運算式。 `eNameExp` 的類型必須 `String`，或是可隱含轉換成 <xref:System.Xml.Linq.XName>的類型。|

  - 表單 `<%= nameExp %>`的內嵌運算式。 `nameExp` 的類型必須 `String` 或可隱含轉換成 <xref:System.Xml.Linq.XName>的類型。 元素的結束記號中不允許內嵌運算式。

- `attributeList`

  選擇性。 常值中宣告的屬性清單。

  `attribute [ attribute ... ]`

  每個 `attribute` 都具有下列其中一個語法：

  - `[aPrefix:]aName=aValue`格式的屬性指派，其中：

    |組件|描述|
    |---|---|
    |`aPrefix`|選擇性。 屬性的 XML 命名空間前置詞。 必須是使用 `Imports` 語句定義的全域 XML 命名空間，或是在此元素或父元素中定義的本機 XML 命名空間。|
    |`aName`|必要。 屬性的名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱宣告[的 XML 元素和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />-表單 `<%= aNameExp %>`的內嵌運算式。 `aNameExp` 的類型必須 `String`，或是可隱含轉換成 <xref:System.Xml.Linq.XName>的類型。|
    |`aValue`|選擇性。 屬性的值。 格式為下列其中一項：<br /><br /> -包含在引號中的常值文字。<br />-表單 `<%= aValueExp %>`的內嵌運算式。 允許任何類型。|

  - 表單 `<%= aExp %>`的內嵌運算式。

- `/>`

  選擇性。 指出元素是空的元素，沒有內容。

- `>`

  必要。 結束開頭或空的元素標記。

- `elementContents`

  選擇性。 元素的內容。

  `content [ content ... ]`

  每個 `content` 都可以是下列其中一項：

  - 常值文字。 如果有任何常值文字，`elementContents` 中的所有空白字元就會變得很重要。

  - 表單 `<%= contentExp %>`的內嵌運算式。

  - XML 元素常值。

  - XML 批註常值。 請參閱[XML 批註常](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)值。

  - XML 處理指示常值。 請參閱[XML 處理指示常](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)值。

  - XML CDATA 常值。 請參閱[XML CDATA 常](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)值。

- `</[name]>`

  選擇性。 表示元素的結束記號。 選擇性的 `name` 參數是內嵌運算式的結果時，不允許使用。

## <a name="return-value"></a>傳回值

<xref:System.Xml.Linq.XElement> 物件。

## <a name="remarks"></a>備註

您可以使用 XML 元素常值語法，在程式碼中建立 <xref:System.Xml.Linq.XElement> 物件。

> [!NOTE]
> XML 常值可以跨越多行，而不需要使用行接續字元。 這項功能可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。

表單 `<%= exp %>` 的內嵌運算式可讓您將動態資訊新增至 XML 元素常值。 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。

Visual Basic 編譯器會將 XML 專案常值轉換成 <xref:System.Xml.Linq.XElement.%23ctor%2A> 的函式的呼叫，如有必要，則會將 <xref:System.Xml.Linq.XAttribute.%23ctor%2A> 的函數。

## <a name="xml-namespaces"></a>XML 命名空間

當您必須在程式碼中多次使用相同命名空間的元素建立 XML 常值時，XML 命名空間前置詞非常有用。 您可以使用全域 XML 命名空間前置詞（使用 `Imports` 語句來定義）或本機前置詞，您可以使用 `xmlns:xmlPrefix="xmlNamespace"` 屬性語法來定義此首碼。 如需詳細資訊，請參閱[Imports 語句（XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。

根據 XML 命名空間的範圍規則，本機前置詞的優先順序高於全域首碼。 不過，如果 XML 常值定義 XML 命名空間，則該命名空間無法供內嵌運算式中出現的運算式使用。 內嵌運算式只能存取全域 XML 命名空間。

Visual Basic 編譯器會將 XML 常值所使用的每個全域 XML 命名空間，轉換成產生的程式碼中的一個本機命名空間定義。 未使用的全域 XML 命名空間不會出現在產生的程式碼中。

## <a name="example"></a>範例

下列範例顯示如何建立具有兩個嵌套空白元素的簡單 XML 專案。

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

此範例會顯示下列文字。 請注意，常值會保留空白元素的結構。

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>範例

下列範例顯示如何使用內嵌運算式來命名專案並建立屬性。

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

此程式碼顯示下列文字：

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>範例

下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後，它會使用命名空間的前置詞來建立 XML 常值，並顯示專案的最終格式。

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

此程式碼顯示下列文字：

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

請注意，編譯器已將全域 XML 命名空間的前置詞，轉換成 XML 命名空間的前置詞定義。 \<ns：中間 > 元素會重新定義 \<ns： inner1 > 專案的 XML 命名空間前置詞。 不過，\<的 ns： inner2 > 元素會使用 `Imports` 語句所定義的命名空間。

## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XElement>
- [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
