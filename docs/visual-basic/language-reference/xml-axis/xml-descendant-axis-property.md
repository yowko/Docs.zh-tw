---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400249"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子代軸屬性 (Visual Basic)

提供下列各項的存取權： <xref:System.Xml.Linq.XElement> 物件、物件 <xref:System.Xml.Linq.XDocument> 、物件的集合 <xref:System.Xml.Linq.XElement> 或物件的集合 <xref:System.Xml.Linq.XDocument> 。

## <a name="syntax"></a>語法

```vb
object...<descendant>
```

## <a name="parts"></a>組件

需要 `object`。 <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。

需要 `...<`。 表示子代軸屬性的開頭。

需要 `descendant`。 要存取的子代節點名稱，格式為 [ `prefix:]name` 。

|部分|描述|
|----------|-----------------|
|`prefix`|選擇性。 子代節點的 XML 命名空間前置詞。 必須是使用語句所定義的全域 XML 命名空間 `Imports` 。|
|`name`|必要。 子代節點的本機名稱。 請參閱宣告[的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|

需要 `>`。 表示子代軸屬性的結尾。

## <a name="return-value"></a>傳回值

<xref:System.Xml.Linq.XElement> 物件的集合。

## <a name="remarks"></a>備註

您可以使用 XML 子系軸屬性 <xref:System.Xml.Linq.XElement> ，從或物件的名稱 <xref:System.Xml.Linq.XDocument> 或從或物件的集合存取下階節點 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> 。 使用 XML `Value` 屬性來存取所傳回集合中第一個子代節點的值。 如需詳細資訊，請參閱[XML Value 屬性](xml-value-property.md)。

Visual Basic 編譯器會將子代軸屬性轉換成方法的呼叫 <xref:System.Xml.Linq.XContainer.Descendants%2A> 。

## <a name="xml-namespaces"></a>XML 命名空間

[子代軸] 屬性中的名稱只能使用以語句全域宣告的 XML 命名空間 `Imports` 。 它無法使用在 XML 專案常值中本機宣告的 XML 命名空間。 如需詳細資訊，請參閱[Imports 語句（XML 命名空間）](../statements/imports-statement-xml-namespace.md)。

## <a name="example"></a>範例

下列範例顯示如何存取名為的第一個子系節點值 `name` ，以及從物件命名的所有子系節點的值 `phone` `contacts` 。

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

此程式碼顯示下列文字：

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>範例

下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後，它會使用命名空間的前置詞來建立 XML 常值，並以限定名稱存取第一個子節點的值 `ns:name` 。

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

此程式碼顯示下列文字：

`Name: Patrick Hines`

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](index.md)
- [XML 常值](../xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
