---
title: ServicePointManager. s_ServicePointTable 欄位
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120005"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="dcd80-102">ServicePointManager\_ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="dcd80-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="dcd80-103">`ServicePointManager.s_ServicePointTable` 是一個 <xref:System.Collections.Hashtable>，其中包含 <xref:System.AppDomain>中的作用中 HTTP 連線（<xref:System.Net.ServicePoint>s）清單。</span><span class="sxs-lookup"><span data-stu-id="dcd80-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcd80-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcd80-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="dcd80-105">[`ServicePointManager.s_ServicePointTable`] 欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="dcd80-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="dcd80-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="dcd80-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcd80-107">需求</span><span class="sxs-lookup"><span data-stu-id="dcd80-107">Requirements</span></span>

<span data-ttu-id="dcd80-108">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dcd80-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dcd80-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="dcd80-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="dcd80-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="dcd80-110">**.NET Framework versions:** Available since 2.0.</span></span>
