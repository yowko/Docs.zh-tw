---
title: Xml (XElement 動態屬性)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920717"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (XElement 動態屬性)

取得項目未格式化的 XML 內容。

## <a name="syntax"></a>語法

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

表示項目未格式化 XML 內容的 <xref:System.String>。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 類別的 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。

## <a name="see-also"></a>請參閱

- [XElement 類別動態屬性](attribute-xelement-dynamic-property.md)
- [值](value-xelement-dynamic-property.md)
