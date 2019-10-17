---
title: SqlStreamChars. Read （Char []，Int32，Int32）方法（SqlTypes）
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395744"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="dacab-102">SqlStreamChars. Read （Char []，Int32，Int32）方法</span><span class="sxs-lookup"><span data-stu-id="dacab-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="dacab-103">在衍生類別中覆寫時，從輸入資料流程讀取下一組字元。</span><span class="sxs-lookup"><span data-stu-id="dacab-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="dacab-104">包含這個方法的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="dacab-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="dacab-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="dacab-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="dacab-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="dacab-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="dacab-107">參數</span><span class="sxs-lookup"><span data-stu-id="dacab-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="dacab-108">要讀取的 char 陣列。</span><span class="sxs-lookup"><span data-stu-id="dacab-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="dacab-109">相對於原點的位移。</span><span class="sxs-lookup"><span data-stu-id="dacab-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="dacab-110">要從目前資料流程讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="dacab-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="dacab-111">Returns</span><span class="sxs-lookup"><span data-stu-id="dacab-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="dacab-112">讀入緩衝區的字元總數。</span><span class="sxs-lookup"><span data-stu-id="dacab-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="dacab-113">備註</span><span class="sxs-lookup"><span data-stu-id="dacab-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="dacab-114">@No__t-0 方法是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="dacab-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dacab-115">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="dacab-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dacab-116">需求</span><span class="sxs-lookup"><span data-stu-id="dacab-116">Requirements</span></span>

<span data-ttu-id="dacab-117">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="dacab-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="dacab-118">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="dacab-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="dacab-119">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="dacab-119">**.NET Framework versions:** Available since 2.0.</span></span>
