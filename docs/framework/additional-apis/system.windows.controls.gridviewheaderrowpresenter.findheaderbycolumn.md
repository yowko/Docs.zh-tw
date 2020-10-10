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
# <a name="findheaderbycolumn-method"></a><span data-ttu-id="9e4b3-103">FindHeaderByColumn 方法</span><span class="sxs-lookup"><span data-stu-id="9e4b3-103">FindHeaderByColumn method</span></span>

<span data-ttu-id="9e4b3-104">尋找視覺化樹狀結構中所指定資料行的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="9e4b3-104">Finds the column header for the specified column in the visual tree.</span></span>

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> <span data-ttu-id="9e4b3-105">這個方法是私用的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="9e4b3-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9e4b3-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="9e4b3-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="9e4b3-107">參數</span><span class="sxs-lookup"><span data-stu-id="9e4b3-107">Parameters</span></span>

<span data-ttu-id="9e4b3-108">`column` <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="9e4b3-108">`column` <xref:System.Windows.Controls.GridViewColumn></span></span>\
<span data-ttu-id="9e4b3-109">應尋找並傳回其標頭的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e4b3-109">The column whose header should be found and returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e4b3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="9e4b3-110">Return value</span></span>

<xref:System.Windows.Controls.GridViewColumnHeader>\
<span data-ttu-id="9e4b3-111">指定之資料行的標頭， `null` 如果指定的資料行不存在，則為。</span><span class="sxs-lookup"><span data-stu-id="9e4b3-111">The header of the specified column, or `null` if the specified column doesn't exist.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e4b3-112">需求</span><span class="sxs-lookup"><span data-stu-id="9e4b3-112">Requirements</span></span>

<span data-ttu-id="9e4b3-113">**命名空間：** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="9e4b3-113">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="9e4b3-114">**元件：** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="9e4b3-114">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="9e4b3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4b3-115">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
