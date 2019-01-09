---
title: ServicePointManager.s_ServicePointTable 欄位
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ebcf5c3f13b3bd30a8e091be09ae546eee1eaffe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147443"
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="8c5c3-102">ServicePointManager.s\_ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="8c5c3-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="8c5c3-103">`ServicePointManager.s_ServicePointTable` 已<xref:System.Collections.Hashtable>，其中包含作用中的 HTTP 連接的清單 (<xref:System.Net.ServicePoint>s) 中<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="8c5c3-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c5c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c5c3-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="8c5c3-105">`ServicePointManager.s_ServicePointTable`欄位是私用，而不是直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="8c5c3-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="8c5c3-106">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="8c5c3-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c5c3-107">需求</span><span class="sxs-lookup"><span data-stu-id="8c5c3-107">Requirements</span></span>

<span data-ttu-id="8c5c3-108">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8c5c3-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8c5c3-109">**組件：**（在 System.dll) 的系統</span><span class="sxs-lookup"><span data-stu-id="8c5c3-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="8c5c3-110">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="8c5c3-110">**.NET Framework versions:** Available since 2.0.</span></span>
