---
title: SqlStreamChars. Dispose （布林值）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395759"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="1323d-102">SqlStreamChars Dispose （布林值）方法</span><span class="sxs-lookup"><span data-stu-id="1323d-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="1323d-103">在衍生類別中覆寫時，釋放資料流程所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="1323d-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="1323d-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="1323d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1323d-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="1323d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1323d-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="1323d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="1323d-107">參數</span><span class="sxs-lookup"><span data-stu-id="1323d-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="1323d-108">`true` 表示釋放 Managed 和 Unmanaged 資源，`false` 則表示只釋放 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="1323d-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="1323d-109">備註</span><span class="sxs-lookup"><span data-stu-id="1323d-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1323d-110">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="1323d-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1323d-111">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="1323d-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1323d-112">需求</span><span class="sxs-lookup"><span data-stu-id="1323d-112">Requirements</span></span>

<span data-ttu-id="1323d-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1323d-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1323d-114">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="1323d-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1323d-115">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="1323d-115">**.NET Framework versions:** Available since 2.0.</span></span>
