---
title: SqlStreamChars.Dispose(Boolean) 方法 (System.Data.SqlTypes)
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
ms.openlocfilehash: cc8df68a608000d89dd322b0d396504483bbf372
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633721"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="f971d-102">SqlStreamChars.Dispose(Boolean) 方法</span><span class="sxs-lookup"><span data-stu-id="f971d-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="f971d-103">當在衍生類別中覆寫時，會釋放資料流所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="f971d-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="f971d-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="f971d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f971d-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="f971d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f971d-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="f971d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="f971d-107">參數</span><span class="sxs-lookup"><span data-stu-id="f971d-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="f971d-108">`true` 表示釋放 Managed 和 Unmanaged 資源，`false` 則表示只釋放 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="f971d-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="f971d-109">備註</span><span class="sxs-lookup"><span data-stu-id="f971d-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f971d-110">`SqlStreamChars.Dispose`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f971d-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f971d-111">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="f971d-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f971d-112">需求</span><span class="sxs-lookup"><span data-stu-id="f971d-112">Requirements</span></span>

<span data-ttu-id="f971d-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f971d-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f971d-114">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="f971d-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f971d-115">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="f971d-115">**.NET Framework versions:** Available since 2.0.</span></span>