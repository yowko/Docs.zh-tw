---
title: SqlStreamChars. SetLength （Int64）方法（SqlTypes）
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
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395730"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="953c4-102">SqlStreamChars. SetLength （Int64）方法</span><span class="sxs-lookup"><span data-stu-id="953c4-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="953c4-103">在衍生類別中覆寫時，釋放資料流程所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="953c4-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="953c4-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="953c4-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="953c4-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="953c4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="953c4-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="953c4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="953c4-107">參數</span><span class="sxs-lookup"><span data-stu-id="953c4-107">Parameters</span></span>

`value`\
<span data-ttu-id="953c4-108">想要的目前資料流長度 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="953c4-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="953c4-109">備註</span><span class="sxs-lookup"><span data-stu-id="953c4-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="953c4-110">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="953c4-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="953c4-111">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="953c4-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="953c4-112">需求</span><span class="sxs-lookup"><span data-stu-id="953c4-112">Requirements</span></span>

<span data-ttu-id="953c4-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="953c4-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="953c4-114">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="953c4-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="953c4-115">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="953c4-115">**.NET Framework versions:** Available since 2.0.</span></span>
