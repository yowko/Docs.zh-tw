---
title: SqlStreamChars.Seek （Int64，SeekOrigin） 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1710c802324920e324b18ddea843f0a532fa0d17
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222983"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="3decc-102">SqlStreamChars.Seek （Int64，SeekOrigin） 方法</span><span class="sxs-lookup"><span data-stu-id="3decc-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="3decc-103">在衍生類別中覆寫時，設定在目前資料流的位置。</span><span class="sxs-lookup"><span data-stu-id="3decc-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="3decc-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="3decc-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="3decc-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="3decc-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="3decc-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="3decc-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="3decc-107">參數</span><span class="sxs-lookup"><span data-stu-id="3decc-107">Parameters</span></span>

`offset`\
<span data-ttu-id="3decc-108">位元組位移，相對於`origin`。</span><span class="sxs-lookup"><span data-stu-id="3decc-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="3decc-109">其中一個列舉值，指出要從中取得新位置的參考點。</span><span class="sxs-lookup"><span data-stu-id="3decc-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="3decc-110">Returns</span><span class="sxs-lookup"><span data-stu-id="3decc-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="3decc-111">目前資料流的新位置。</span><span class="sxs-lookup"><span data-stu-id="3decc-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="3decc-112">備註</span><span class="sxs-lookup"><span data-stu-id="3decc-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="3decc-113">`SqlStreamChars.Seek`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="3decc-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3decc-114">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="3decc-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3decc-115">需求</span><span class="sxs-lookup"><span data-stu-id="3decc-115">Requirements</span></span>

<span data-ttu-id="3decc-116">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="3decc-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="3decc-117">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="3decc-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="3decc-118">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="3decc-118">**.NET Framework versions:** Available since 2.0.</span></span>