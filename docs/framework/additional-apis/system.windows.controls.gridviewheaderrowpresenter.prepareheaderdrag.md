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
# <a name="prepareheaderdrag-method"></a><span data-ttu-id="f88c4-103">PrepareHeaderDrag 方法</span><span class="sxs-lookup"><span data-stu-id="f88c4-103">PrepareHeaderDrag method</span></span>

<span data-ttu-id="f88c4-104">準備要重新排序的指定資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="f88c4-104">Prepares the specified column header for reordering.</span></span>

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> <span data-ttu-id="f88c4-105">這個方法是私用的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f88c4-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f88c4-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f88c4-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="f88c4-107">參數</span><span class="sxs-lookup"><span data-stu-id="f88c4-107">Parameters</span></span>

<span data-ttu-id="f88c4-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span><span class="sxs-lookup"><span data-stu-id="f88c4-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span></span>\
<span data-ttu-id="f88c4-109">要準備重新排序的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="f88c4-109">The column header to prepare for reordering.</span></span>

<span data-ttu-id="f88c4-110">`pos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="f88c4-110">`pos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="f88c4-111">從開始拖曳的位置（相對於 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> ）。</span><span class="sxs-lookup"><span data-stu-id="f88c4-111">The position, relative to <xref:System.Windows.Controls.GridViewHeaderRowPresenter>, where the dragging starts.</span></span>

<span data-ttu-id="f88c4-112">`relativePos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="f88c4-112">`relativePos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="f88c4-113">從開始拖曳的位置（相對於 `header` ）。</span><span class="sxs-lookup"><span data-stu-id="f88c4-113">The position, relative to `header`, where the dragging starts.</span></span>

<span data-ttu-id="f88c4-114">`cancelInvoke` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="f88c4-114">`cancelInvoke` <xref:System.Boolean></span></span>\
<span data-ttu-id="f88c4-115">`true` 取消重新排列;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f88c4-115">`true` to cancel the reordering; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f88c4-116">需求</span><span class="sxs-lookup"><span data-stu-id="f88c4-116">Requirements</span></span>

<span data-ttu-id="f88c4-117">**命名空間：** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="f88c4-117">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="f88c4-118">**元件：** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="f88c4-118">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="f88c4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f88c4-119">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
