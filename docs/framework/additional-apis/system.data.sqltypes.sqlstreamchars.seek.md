---
title: SqlStreamChars。 Seek （Int64，SeekOrigin）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395589"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="0cc1a-102">SqlStreamChars。 Seek （Int64，SeekOrigin）方法</span><span class="sxs-lookup"><span data-stu-id="0cc1a-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="0cc1a-103">在衍生類別中覆寫時，設定在目前資料流的位置。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="0cc1a-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0cc1a-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0cc1a-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="0cc1a-107">參數</span><span class="sxs-lookup"><span data-stu-id="0cc1a-107">Parameters</span></span>

`offset`\
<span data-ttu-id="0cc1a-108">相對於 `origin` 的位元組位移。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="0cc1a-109">其中一個列舉值，表示要從中取得新位置的參考點。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="0cc1a-110">Returns</span><span class="sxs-lookup"><span data-stu-id="0cc1a-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="0cc1a-111">目前資料流的新位置。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cc1a-112">備註</span><span class="sxs-lookup"><span data-stu-id="0cc1a-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0cc1a-113">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0cc1a-114">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cc1a-115">需求</span><span class="sxs-lookup"><span data-stu-id="0cc1a-115">Requirements</span></span>

<span data-ttu-id="0cc1a-116">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0cc1a-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0cc1a-117">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="0cc1a-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0cc1a-118">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="0cc1a-118">**.NET Framework versions:** Available since 2.0.</span></span>
