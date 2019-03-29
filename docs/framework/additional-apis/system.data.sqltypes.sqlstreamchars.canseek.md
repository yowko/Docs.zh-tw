---
title: SqlStreamChars.CanSeek 屬性 (System.Data.SqlTypes)
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
ms.openlocfilehash: 52f88a3551e20c74d7a1144c3cd6859a023980db
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633708"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="41e5b-102">SqlStreamChars.CanSeek 屬性</span><span class="sxs-lookup"><span data-stu-id="41e5b-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="41e5b-103">當在衍生類別中覆寫時，取得值，指出目前資料流是否支援搜尋作業。</span><span class="sxs-lookup"><span data-stu-id="41e5b-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="41e5b-104">包含此屬性的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="41e5b-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="41e5b-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="41e5b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="41e5b-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="41e5b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="41e5b-107">屬性值</span><span class="sxs-lookup"><span data-stu-id="41e5b-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="41e5b-108">`true` 如果目前資料流支援搜尋作業。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="41e5b-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="41e5b-109">備註</span><span class="sxs-lookup"><span data-stu-id="41e5b-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="41e5b-110">`SqlStreamChars.CanSeek`屬性是 private，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="41e5b-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="41e5b-111">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="41e5b-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="41e5b-112">需求</span><span class="sxs-lookup"><span data-stu-id="41e5b-112">Requirements</span></span>

<span data-ttu-id="41e5b-113">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="41e5b-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="41e5b-114">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="41e5b-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="41e5b-115">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="41e5b-115">**.NET Framework versions:** Available since 2.0.</span></span>