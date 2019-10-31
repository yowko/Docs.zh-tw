---
title: ServicePoint. m_ConnectionGroupList 欄位
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1991dae4d03f617857b860f920077531f7937bf1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120052"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="36d15-102">ServicePoint\_ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="36d15-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="36d15-103">`ServicePoint.m_ConnectionGroupList` 是連線群組的 <xref:System.Collections.Hashtable>，每個都持有 <xref:System.Net.ServicePoint>URI 的連接。</span><span class="sxs-lookup"><span data-stu-id="36d15-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="36d15-104">語法</span><span class="sxs-lookup"><span data-stu-id="36d15-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="36d15-105">[`ServicePoint.m_ConnectionGroupList`] 欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="36d15-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="36d15-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="36d15-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="36d15-107">需求</span><span class="sxs-lookup"><span data-stu-id="36d15-107">Requirements</span></span>

<span data-ttu-id="36d15-108">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="36d15-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="36d15-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="36d15-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="36d15-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="36d15-110">**.NET Framework versions:** Available since 2.0.</span></span>
