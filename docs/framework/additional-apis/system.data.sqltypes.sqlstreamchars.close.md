---
title: SqlStreamChars.Close 方法 (System.Data.SqlTypes)
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
ms.openlocfilehash: d0c29bbc5c6bea98cf36e3c2b6bf7825d6843ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705866"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="0efdd-102">SqlStreamChars.Close 方法</span><span class="sxs-lookup"><span data-stu-id="0efdd-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="0efdd-103">關閉目前的資料流，並釋放任何與資料流相關聯的系統資源。</span><span class="sxs-lookup"><span data-stu-id="0efdd-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="0efdd-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="0efdd-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0efdd-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="0efdd-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="0efdd-106"> 其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="0efdd-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="0efdd-107">備註</span><span class="sxs-lookup"><span data-stu-id="0efdd-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0efdd-108">`SqlStreamChars.Close`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="0efdd-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0efdd-109">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="0efdd-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0efdd-110">需求</span><span class="sxs-lookup"><span data-stu-id="0efdd-110">Requirements</span></span>

<span data-ttu-id="0efdd-111">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0efdd-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0efdd-112">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="0efdd-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0efdd-113">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="0efdd-113">**.NET Framework versions:** Available since 2.0.</span></span>