---
title: SqlStreamChars. CanSeek 屬性（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395771"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="d8fe7-102">SqlStreamChars. CanSeek 屬性</span><span class="sxs-lookup"><span data-stu-id="d8fe7-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="d8fe7-103">在衍生類別中覆寫時，取得值，指出目前的資料流程是否支援搜尋作業。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="d8fe7-104">包含此屬性的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d8fe7-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d8fe7-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="d8fe7-107">屬性值</span><span class="sxs-lookup"><span data-stu-id="d8fe7-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="d8fe7-108">如果目前的流支援搜尋作業，則 `true`：否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8fe7-109">備註</span><span class="sxs-lookup"><span data-stu-id="d8fe7-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d8fe7-110">@No__t-0 屬性是私用的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d8fe7-111">在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8fe7-112">需求</span><span class="sxs-lookup"><span data-stu-id="d8fe7-112">Requirements</span></span>

<span data-ttu-id="d8fe7-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d8fe7-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d8fe7-114">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="d8fe7-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d8fe7-115">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="d8fe7-115">**.NET Framework versions:** Available since 2.0.</span></span>
