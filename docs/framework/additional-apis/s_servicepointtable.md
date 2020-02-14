---
title: ServicePointManager。 s_ServicePointTable 欄位
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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214925"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="c0a6e-102">ServicePointManager\_ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="c0a6e-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="c0a6e-103">`ServicePointManager.s_ServicePointTable` 是一個 <xref:System.Collections.Hashtable>，其中包含 <xref:System.AppDomain>中的作用中 HTTP 連線（<xref:System.Net.ServicePoint>s）清單。</span><span class="sxs-lookup"><span data-stu-id="c0a6e-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0a6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0a6e-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="c0a6e-105">[`ServicePointManager.s_ServicePointTable`] 欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="c0a6e-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="c0a6e-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="c0a6e-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0a6e-107">需求</span><span class="sxs-lookup"><span data-stu-id="c0a6e-107">Requirements</span></span>

<span data-ttu-id="c0a6e-108">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c0a6e-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c0a6e-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="c0a6e-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c0a6e-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="c0a6e-110">**.NET Framework versions:** Available since 2.0.</span></span>
