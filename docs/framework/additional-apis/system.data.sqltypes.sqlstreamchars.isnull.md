---
title: SqlStreamChars.IsNull 屬性 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7d2a2cf66ce2a375b1e5989b2fb6ddc9e3d94411
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825442"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="2c671-102">SqlStreamChars.IsNull 屬性</span><span class="sxs-lookup"><span data-stu-id="2c671-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="2c671-103">當在衍生類別中覆寫時，取得值，指出資料流是否`null`。</span><span class="sxs-lookup"><span data-stu-id="2c671-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="2c671-104">包含此屬性的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="2c671-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2c671-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="2c671-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="2c671-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="2c671-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c671-107">語法</span><span class="sxs-lookup"><span data-stu-id="2c671-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="2c671-108">屬性值</span><span class="sxs-lookup"><span data-stu-id="2c671-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="2c671-109">`true` 如果資料流`null`; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="2c671-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c671-110">備註</span><span class="sxs-lookup"><span data-stu-id="2c671-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2c671-111">`SqlStreamChars.IsNull`屬性是 private，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="2c671-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2c671-112">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="2c671-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c671-113">需求</span><span class="sxs-lookup"><span data-stu-id="2c671-113">Requirements</span></span>

<span data-ttu-id="2c671-114">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="2c671-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="2c671-115">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="2c671-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2c671-116">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="2c671-116">**.NET Framework versions:** Available since 2.0.</span></span>