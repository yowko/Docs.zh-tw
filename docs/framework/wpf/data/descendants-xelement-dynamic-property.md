---
title: Descendants (XElement 動態屬性)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920885"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (XElement 動態屬性)

取得用於擷取目前項目 (符合指定的擴充名稱) 之所有子代項目的索引子 (Indexer)。

## <a name="syntax"></a>語法

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用指定之子代項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。

傳回集合中的項目順序為 XML 來源文件的順序。

這個屬性會使用延後執行。

## <a name="see-also"></a>請參閱

- [XElement 類別動態屬性](attribute-xelement-dynamic-property.md)
- [項目](elements-xelement-dynamic-property.md)
