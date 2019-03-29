---
title: SqlStreamChars.Length 屬性 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c2ef66fa493512e1fa062e22858ea251ced39453
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634137"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="e3960-102">SqlStreamChars.Length 屬性</span><span class="sxs-lookup"><span data-stu-id="e3960-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="e3960-103">當在衍生類別中覆寫時，取得目前資料流的長度。</span><span class="sxs-lookup"><span data-stu-id="e3960-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="e3960-104">包含此屬性的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="e3960-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e3960-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="e3960-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e3960-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="e3960-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3960-107">語法</span><span class="sxs-lookup"><span data-stu-id="e3960-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="e3960-108">屬性值</span><span class="sxs-lookup"><span data-stu-id="e3960-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="e3960-109">資料流的長度。</span><span class="sxs-lookup"><span data-stu-id="e3960-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3960-110">備註</span><span class="sxs-lookup"><span data-stu-id="e3960-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e3960-111">`SqlStreamChars.Length`屬性是 private，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="e3960-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e3960-112">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="e3960-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3960-113">需求</span><span class="sxs-lookup"><span data-stu-id="e3960-113">Requirements</span></span>

<span data-ttu-id="e3960-114">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e3960-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e3960-115">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="e3960-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e3960-116">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="e3960-116">**.NET Framework versions:** Available since 2.0.</span></span>