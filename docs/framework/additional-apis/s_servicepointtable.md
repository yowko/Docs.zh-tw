---
title: 服務點管理器.s_ServicePointTable欄位
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155805"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="39846-102">服務點管理器的服務\_點表字段</span><span class="sxs-lookup"><span data-stu-id="39846-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="39846-103">`ServicePointManager.s_ServicePointTable`是<xref:System.Collections.Hashtable>包含 中的活動 HTTP 連接的清單<xref:System.Net.ServicePoint>的<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="39846-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="39846-104">語法</span><span class="sxs-lookup"><span data-stu-id="39846-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="39846-105">該`ServicePointManager.s_ServicePointTable`欄位是私有的，不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="39846-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="39846-106">在任何情況下，Microsoft 都不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="39846-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="39846-107">需求</span><span class="sxs-lookup"><span data-stu-id="39846-107">Requirements</span></span>

<span data-ttu-id="39846-108">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="39846-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="39846-109">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="39846-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="39846-110">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="39846-110">**.NET Framework versions:** Available since 2.0.</span></span>
