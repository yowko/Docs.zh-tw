---
title: SqlStreamChars. Length 屬性（SqlTypes）
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
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395612"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="8ab91-102">SqlStreamChars. Length 屬性</span><span class="sxs-lookup"><span data-stu-id="8ab91-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="8ab91-103">在衍生類別中覆寫時，取得目前資料流程的長度。</span><span class="sxs-lookup"><span data-stu-id="8ab91-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="8ab91-104">包含此屬性的元件與 SQLAccess 具有 friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="8ab91-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="8ab91-105">其目的是要供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="8ab91-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="8ab91-106">若為其他資料庫，請使用該資料庫所提供的裝載機制。</span><span class="sxs-lookup"><span data-stu-id="8ab91-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ab91-107">語法</span><span class="sxs-lookup"><span data-stu-id="8ab91-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="8ab91-108">屬性值</span><span class="sxs-lookup"><span data-stu-id="8ab91-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="8ab91-109">資料流的長度。</span><span class="sxs-lookup"><span data-stu-id="8ab91-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ab91-110">備註</span><span class="sxs-lookup"><span data-stu-id="8ab91-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8ab91-111">@No__t-0 屬性是私用的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="8ab91-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8ab91-112">在任何情況下，Microsoft 不支援在生產應用程式中使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="8ab91-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ab91-113">需求</span><span class="sxs-lookup"><span data-stu-id="8ab91-113">Requirements</span></span>

<span data-ttu-id="8ab91-114">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="8ab91-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="8ab91-115">**元件：** System.web （在 System.web 中）</span><span class="sxs-lookup"><span data-stu-id="8ab91-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="8ab91-116">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="8ab91-116">**.NET Framework versions:** Available since 2.0.</span></span>
