---
title: ICLRDataEnumMemoryRegionsCallback 介面
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e7ce243658a8c8a8404ff9079ed1395e56486f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604142"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="902aa-102">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="902aa-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="902aa-103">提供回呼方法，以便[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="902aa-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="902aa-104">方法</span><span class="sxs-lookup"><span data-stu-id="902aa-104">Methods</span></span>  
  
|<span data-ttu-id="902aa-105">方法</span><span class="sxs-lookup"><span data-stu-id="902aa-105">Method</span></span>|<span data-ttu-id="902aa-106">描述</span><span class="sxs-lookup"><span data-stu-id="902aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="902aa-107">EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="902aa-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="902aa-108">由呼叫`ICLRDataEnumMemoryRegions::EnumMemoryRegions`偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="902aa-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="902aa-109">需求</span><span class="sxs-lookup"><span data-stu-id="902aa-109">Requirements</span></span>  
 <span data-ttu-id="902aa-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="902aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902aa-111">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="902aa-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="902aa-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="902aa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="902aa-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="902aa-114">See also</span></span>
- [<span data-ttu-id="902aa-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="902aa-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
