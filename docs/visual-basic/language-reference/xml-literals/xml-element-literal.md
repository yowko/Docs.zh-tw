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
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400185"
---
# <a name="xml-element-literal-visual-basic"></a>XML 項目常值 (Visual Basic)

代表物件的常值 <xref:System.Xml.Linq.XElement> 。

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

  - 元素名稱的常值文字，格式為 `[ePrefix:]eName` ，其中：

    |部分|描述|
    |---|---|
    |`ePrefix`|選擇性。 元素的 XML 命名空間前置詞。 必須是以檔案中的語句或在專案層級定義的全域 XML 命名空間 `Imports` ，或是在這個元素或父元素中定義的本機 XML 命名空間。|
    |`eName`|必要。 元素名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱宣告[的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />-表單的內嵌運算式 `<%= eNameExp %>` 。 的類型 `eNameExp` 必須是 `String` 或可隱含轉換成的類型 <xref:System.Xml.Linq.XName> 。|

  - 表單的內嵌運算式 `<%= nameExp %>` 。 的類型 `nameExp` 必須是 `String` 或可隱含轉換成的類型 <xref:System.Xml.Linq.XName> 。 元素的結束記號中不允許內嵌運算式。

- `attributeList`

  選擇性。 常值中宣告的屬性清單。

  `attribute [ attribute ... ]`

  每個 `attribute` 都具有下列其中一個語法：

  - 屬性指派，格式為 `[aPrefix:]aName=aValue` ，其中：

    |部分|描述|
    |---|---|
    |`aPrefix`|選擇性。 屬性的 XML 命名空間前置詞。 必須是使用語句定義的全域 XML 命名空間 `Imports` ，或是在此元素或父元素中定義的本機 XML 命名空間。|
    |`aName`|必要。 屬性的名稱。 格式為下列其中一項：<br /><br /> -常值文字。 請參閱宣告[的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />-表單的內嵌運算式 `<%= aNameExp %>` 。 的類型 `aNameExp` 必須是 `String` 或可隱含轉換成的類型 <xref:System.Xml.Linq.XName> 。|
    |`aValue`|選擇性。 屬性的值。 格式為下列其中一項：<br /><br /> -包含在引號中的常值文字。<br />-表單的內嵌運算式 `<%= aValueExp %>` 。 允許任何類型。|

  - 表單的內嵌運算式 `<%= aExp %>` 。

- `/>`

  選擇性。 指出元素是空的元素，沒有內容。

- `>`

  必要。 結束開頭或空的元素標記。

- `elementContents`

  選擇性。 元素的內容。

  `content [ content ... ]`

  每個都 `content` 可以是下列其中一項：

  - 常值文字。 `elementContents`如果有任何常值文字，中的所有空白字元都會變得很明顯。

  - 表單的內嵌運算式 `<%= contentExp %>` 。

  - XML 元素常值。

  - XML 批註常值。 請參閱[XML 批註常](xml-comment-literal.md)值。

  - XML 處理指示常值。 請參閱[XML 處理指示常](xml-processing-instruction-literal.md)值。

  - XML CDATA 常值。 請參閱[XML CDATA 常](xml-cdata-literal.md)值。

- `</[name]>`

  選擇性。 表示元素的結束記號。 `name`如果是內嵌運算式的結果，則不允許選擇性參數。

## <a name="return-value"></a>傳回值

<xref:System.Xml.Linq.XElement> 物件。

## <a name="remarks"></a>備註

您可以使用 XML 元素常值語法， <xref:System.Xml.Linq.XElement> 在您的程式碼中建立物件。

> [!NOTE]
> XML 常值可以跨越多行，而不需要使用行接續字元。 這項功能可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。

表單的內嵌運算式可 `<%= exp %>` 讓您將動態資訊新增至 XML 元素常值。 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)。

Visual Basic 編譯器會將 XML 專案常值轉換成對此函式的呼叫， <xref:System.Xml.Linq.XElement.%23ctor%2A> 如有需要，則會將它轉換為 <xref:System.Xml.Linq.XAttribute.%23ctor%2A> 函數。

## <a name="xml-namespaces"></a>XML 命名空間

當您必須在程式碼中多次使用相同命名空間的元素建立 XML 常值時，XML 命名空間前置詞非常有用。 您可以使用全域 XML 命名空間前置詞，這是使用 `Imports` 語句或使用屬性語法定義的本機前置詞所定義 `xmlns:xmlPrefix="xmlNamespace"` 。 如需詳細資訊，請參閱[Imports 語句（XML 命名空間）](../statements/imports-statement-xml-namespace.md)。

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

請注意，編譯器已將全域 XML 命名空間的前置詞，轉換成 XML 命名空間的前置詞定義。 元素會重新 \<ns:middle> 定義元素的 XML 命名空間前置詞 \<ns:inner1> 。 不過， \<ns:inner2> 元素會使用語句所定義的命名空間 `Imports` 。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [宣告的 XML 項目和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML 文件常值](xml-comment-literal.md)
- [XML CDATA 常值](xml-cdata-literal.md)
- [XML 常值](index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports 陳述式 (XML 命名空間)](../statements/imports-statement-xml-namespace.md)
