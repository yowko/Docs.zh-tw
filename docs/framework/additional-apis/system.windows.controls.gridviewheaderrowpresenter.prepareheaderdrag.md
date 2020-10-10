---
title: 'PrepareHeaderDrag 方法 (GridViewHeaderRowPresenter) '
description: 瞭解稱為 PrepareHeaderDrag 的私用 WPF 方法。
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 6d806b8a50de3234cd04198f4ab86621dcd6ede1
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877742"
---
# <a name="prepareheaderdrag-method"></a>PrepareHeaderDrag 方法

準備要重新排序的指定資料行標頭。

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> 這個方法是私用的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="parameters"></a>參數

`header` <xref:System.Windows.Controls.GridViewColumnHeader>\
要準備重新排序的資料行標題。

`pos` <xref:System.Windows.Point>\
從開始拖曳的位置（相對於 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> ）。

`relativePos` <xref:System.Windows.Point>\
從開始拖曳的位置（相對於 `header` ）。

`cancelInvoke` <xref:System.Boolean>\
`true` 取消重新排列;否則為 `false` 。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Windows.Controls>

**元件：** PresentationFramework.dll

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
