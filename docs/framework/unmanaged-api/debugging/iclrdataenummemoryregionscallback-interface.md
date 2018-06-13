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
ms.openlocfilehash: 0a0af0c86bc44a4968119e1afd2a84e17e941601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405495"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="797de-102">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="797de-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="797de-103">提供回呼方法，以便[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)以偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="797de-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="797de-104">方法</span><span class="sxs-lookup"><span data-stu-id="797de-104">Methods</span></span>  
  
|<span data-ttu-id="797de-105">方法</span><span class="sxs-lookup"><span data-stu-id="797de-105">Method</span></span>|<span data-ttu-id="797de-106">描述</span><span class="sxs-lookup"><span data-stu-id="797de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="797de-107">EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="797de-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="797de-108">由呼叫`ICLRDataEnumMemoryRegions::EnumMemoryRegions`以偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="797de-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="797de-109">需求</span><span class="sxs-lookup"><span data-stu-id="797de-109">Requirements</span></span>  
 <span data-ttu-id="797de-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="797de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="797de-111">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="797de-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="797de-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="797de-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="797de-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="797de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797de-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="797de-114">See Also</span></span>  
 [<span data-ttu-id="797de-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="797de-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
