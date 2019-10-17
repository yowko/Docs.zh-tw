---
title: SqlStreamChars. Write （Char []，Int32，Int32）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395580"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="349db-102">SqlStreamChars. Write （Char []，Int32，Int32）方法</span><span class="sxs-lookup"><span data-stu-id="349db-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="349db-103">在衍生類別中覆寫時，將一連串的字元寫入目前的資料流程，並將此資料流程中目前的位置前移寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="349db-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="349db-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="349db-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="349db-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="349db-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="349db-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="349db-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="349db-107">參數</span><span class="sxs-lookup"><span data-stu-id="349db-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="349db-108">要寫入的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="349db-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="349db-109">相對於原點的位移。</span><span class="sxs-lookup"><span data-stu-id="349db-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="349db-110">要寫入目前資料流程的字元數。</span><span class="sxs-lookup"><span data-stu-id="349db-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="349db-111">備註</span><span class="sxs-lookup"><span data-stu-id="349db-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="349db-112">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="349db-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="349db-113">在任何情況下，Microsoft 不支援使用此方法在生產應用程式中寫入。</span><span class="sxs-lookup"><span data-stu-id="349db-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="349db-114">需求</span><span class="sxs-lookup"><span data-stu-id="349db-114">Requirements</span></span>

<span data-ttu-id="349db-115">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="349db-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="349db-116">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="349db-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="349db-117">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="349db-117">**.NET Framework versions:** Available since 2.0.</span></span>
