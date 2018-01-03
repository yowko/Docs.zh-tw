---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1685b1f739519485e5e68928b29a874587e6f9c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="e8993-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法</span><span class="sxs-lookup"><span data-stu-id="e8993-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="e8993-103">列舉指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="e8993-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8993-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8993-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8993-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8993-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="e8993-106">[in]指標[ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)會呼叫這個方法來通知結果的偵錯工具正在列舉每個記憶體區域的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8993-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="e8993-107">即使回呼表示失敗，還是會繼續記憶體區域的列舉。</span><span class="sxs-lookup"><span data-stu-id="e8993-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="e8993-108">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="e8993-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="e8993-109">[in]值為[CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)列舉，指定要列舉的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="e8993-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8993-110">備註</span><span class="sxs-lookup"><span data-stu-id="e8993-110">Remarks</span></span>  
 <span data-ttu-id="e8993-111">這個方法會使用指定[ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)通知結果的呼叫端的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8993-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8993-112">需求</span><span class="sxs-lookup"><span data-stu-id="e8993-112">Requirements</span></span>  
 <span data-ttu-id="e8993-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8993-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8993-114">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e8993-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e8993-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8993-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8993-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8993-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8993-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8993-117">See Also</span></span>  
 [<span data-ttu-id="e8993-118">ICLRDataEnumMemoryRegions 介面</span><span class="sxs-lookup"><span data-stu-id="e8993-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
