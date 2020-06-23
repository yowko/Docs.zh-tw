---
title: ServicePointManager。 s_ServicePointTable] 欄位
description: 閱讀 .NET 中 s_ServicePointTable ServicePointManager 欄位的相關資訊。 此雜湊表欄位包含 AppDomain 中的作用中 HTTP 連接（ServicePoints）。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989540"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="b63e2-104">ServicePointManager. s \_ ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="b63e2-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="b63e2-105">`ServicePointManager.s_ServicePointTable`是 <xref:System.Collections.Hashtable> ，其中包含中的使用中 HTTP 連接清單 <xref:System.Net.ServicePoint> <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="b63e2-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="b63e2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b63e2-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="b63e2-107">`ServicePointManager.s_ServicePointTable`欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="b63e2-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b63e2-108">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="b63e2-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b63e2-109">需求</span><span class="sxs-lookup"><span data-stu-id="b63e2-109">Requirements</span></span>

<span data-ttu-id="b63e2-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b63e2-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b63e2-111">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="b63e2-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b63e2-112">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="b63e2-112">**.NET Framework versions:** Available since 2.0.</span></span>
