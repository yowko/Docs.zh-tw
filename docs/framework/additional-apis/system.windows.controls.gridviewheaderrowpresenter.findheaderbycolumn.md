---
title: 'FindHeaderByColumn 方法 (GridViewHeaderRowPresenter) '
description: 瞭解稱為 FindHeaderByColumn 的私用 WPF 方法。
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 88ed2928f86602d1078488354de6d5267c0311f5
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877747"
---
# <a name="findheaderbycolumn-method"></a>FindHeaderByColumn 方法

尋找視覺化樹狀結構中所指定資料行的資料行標頭。

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> 這個方法是私用的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="parameters"></a>參數

`column` <xref:System.Windows.Controls.GridViewColumn>\
應尋找並傳回其標頭的資料行。

## <a name="return-value"></a>傳回值

<xref:System.Windows.Controls.GridViewColumnHeader>\
指定之資料行的標頭， `null` 如果指定的資料行不存在，則為。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Windows.Controls>

**元件：** PresentationFramework.dll

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
