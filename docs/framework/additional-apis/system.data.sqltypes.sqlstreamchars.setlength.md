---
title: SqlStreamChars.SetLength(Int64) 方法 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1283fea83cf77bbc898d460feedc72b898a65fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675166"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="4228d-102">SqlStreamChars.SetLength(Int64) 方法</span><span class="sxs-lookup"><span data-stu-id="4228d-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="4228d-103">當在衍生類別中覆寫時，會釋放資料流所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="4228d-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="4228d-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="4228d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="4228d-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="4228d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="4228d-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="4228d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="4228d-107">參數</span><span class="sxs-lookup"><span data-stu-id="4228d-107">Parameters</span></span>

`value`\
<span data-ttu-id="4228d-108">想要的目前資料流長度 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="4228d-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="4228d-109">備註</span><span class="sxs-lookup"><span data-stu-id="4228d-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4228d-110">`SqlStreamChars.SetLength`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="4228d-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4228d-111">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="4228d-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4228d-112">需求</span><span class="sxs-lookup"><span data-stu-id="4228d-112">Requirements</span></span>

<span data-ttu-id="4228d-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="4228d-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="4228d-114">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="4228d-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="4228d-115">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="4228d-115">**.NET Framework versions:** Available since 2.0.</span></span>