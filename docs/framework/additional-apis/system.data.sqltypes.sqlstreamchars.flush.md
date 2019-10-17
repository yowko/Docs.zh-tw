---
title: SqlStreamChars. Flush 方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395617"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="d1190-102">SqlStreamChars. Flush 方法</span><span class="sxs-lookup"><span data-stu-id="d1190-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="d1190-103">當在衍生類別中覆寫時，會清除這個資料流的所有緩衝區，並造成所有緩衝資料都寫入基礎裝置。</span><span class="sxs-lookup"><span data-stu-id="d1190-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="d1190-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="d1190-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d1190-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="d1190-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d1190-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="d1190-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1190-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1190-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="d1190-108">備註</span><span class="sxs-lookup"><span data-stu-id="d1190-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d1190-109">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="d1190-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d1190-110">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="d1190-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1190-111">需求</span><span class="sxs-lookup"><span data-stu-id="d1190-111">Requirements</span></span>

<span data-ttu-id="d1190-112">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d1190-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d1190-113">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="d1190-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d1190-114">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="d1190-114">**.NET Framework versions:** Available since 2.0.</span></span>
