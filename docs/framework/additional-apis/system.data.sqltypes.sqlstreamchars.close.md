---
title: SqlStreamChars.Close 方法 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 634b2262ce3262b2c5971fb995b7c988f50924ed
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826885"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="f9828-102">SqlStreamChars.Close 方法</span><span class="sxs-lookup"><span data-stu-id="f9828-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="f9828-103">關閉目前的資料流，並釋放任何與資料流相關聯的系統資源。</span><span class="sxs-lookup"><span data-stu-id="f9828-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="f9828-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="f9828-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f9828-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="f9828-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="f9828-106"> 其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="f9828-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="f9828-107">備註</span><span class="sxs-lookup"><span data-stu-id="f9828-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f9828-108">`SqlStreamChars.Close`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f9828-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f9828-109">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="f9828-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9828-110">需求</span><span class="sxs-lookup"><span data-stu-id="f9828-110">Requirements</span></span>

<span data-ttu-id="f9828-111">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f9828-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f9828-112">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="f9828-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f9828-113">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="f9828-113">**.NET Framework versions:** Available since 2.0.</span></span>