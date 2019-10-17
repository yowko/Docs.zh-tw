---
title: SqlStreamChars. Close 方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395628"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="c7b33-102">SqlStreamChars. Close 方法</span><span class="sxs-lookup"><span data-stu-id="c7b33-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="c7b33-103">關閉目前的資料流程，並釋放任何與資料流程相關聯的系統資源。</span><span class="sxs-lookup"><span data-stu-id="c7b33-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="c7b33-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="c7b33-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="c7b33-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="c7b33-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="c7b33-106"> 若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="c7b33-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="c7b33-107">備註</span><span class="sxs-lookup"><span data-stu-id="c7b33-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c7b33-108">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="c7b33-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c7b33-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="c7b33-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7b33-110">需求</span><span class="sxs-lookup"><span data-stu-id="c7b33-110">Requirements</span></span>

<span data-ttu-id="c7b33-111">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="c7b33-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="c7b33-112">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="c7b33-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="c7b33-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="c7b33-113">**.NET Framework versions:** Available since 2.0.</span></span>
