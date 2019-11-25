---
title: MemoryStream. InternalGetOriginAndLength 方法（System.IO）
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284028"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>MemoryStream. InternalGetOriginAndLength 方法

取得記憶體資料流程來源和長度的內部值。

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>參數

- `origin` <xref:System.Int32>\
  當這個方法傳回時，就是建立新的 <xref:System.IO.MemoryStream> 物件時，所指定之位元組陣列的位移。 如果位元組陣列是由 <xref:System.IO.MemoryStream>所建立，則包含0。

- `length` <xref:System.Int32>\
  當這個方法傳回時，就是記憶體資料流程內的位元組數目。

## <a name="remarks"></a>備註

> [!WARNING]
> `MemoryStream.InternalGetOriginAndLength` 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.IO>

**元件：** mscorlib （在 mscorlib.dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
