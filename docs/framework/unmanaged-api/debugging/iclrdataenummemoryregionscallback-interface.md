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
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122918"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="88fad-102">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="88fad-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="88fad-103">提供[ICLRDataEnumMemoryRegions：： EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)的回呼方法，向偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="88fad-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88fad-104">方法</span><span class="sxs-lookup"><span data-stu-id="88fad-104">Methods</span></span>  
  
|<span data-ttu-id="88fad-105">方法</span><span class="sxs-lookup"><span data-stu-id="88fad-105">Method</span></span>|<span data-ttu-id="88fad-106">描述</span><span class="sxs-lookup"><span data-stu-id="88fad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88fad-107">EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="88fad-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="88fad-108">由 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` 呼叫以向偵錯工具報告，這是嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="88fad-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88fad-109">需求</span><span class="sxs-lookup"><span data-stu-id="88fad-109">Requirements</span></span>  
 <span data-ttu-id="88fad-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88fad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88fad-111">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="88fad-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="88fad-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88fad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88fad-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88fad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fad-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="88fad-114">See also</span></span>

- [<span data-ttu-id="88fad-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="88fad-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
