---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 886f78a0561ebbd5470b7932123f67975d650693
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197343"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="54b9c-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法</span><span class="sxs-lookup"><span data-stu-id="54b9c-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="54b9c-103">列舉指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="54b9c-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="54b9c-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54b9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="54b9c-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="54b9c-106">[in]指標[ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)會呼叫這個方法來通知結果的偵錯工具正在列舉每個記憶體區域的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54b9c-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="54b9c-107">即使回呼表示失敗，仍會繼續記憶體區域的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="54b9c-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="54b9c-108">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="54b9c-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="54b9c-109">[in]值為[CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)列舉，指定要列舉的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="54b9c-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54b9c-110">備註</span><span class="sxs-lookup"><span data-stu-id="54b9c-110">Remarks</span></span>  
 <span data-ttu-id="54b9c-111">這個方法會使用指定[ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)通知結果的呼叫端的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54b9c-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54b9c-112">需求</span><span class="sxs-lookup"><span data-stu-id="54b9c-112">Requirements</span></span>  
 <span data-ttu-id="54b9c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54b9c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b9c-114">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="54b9c-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="54b9c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54b9c-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="54b9c-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="54b9c-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54b9c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54b9c-117">See also</span></span>

- [<span data-ttu-id="54b9c-118">ICLRDataEnumMemoryRegions 介面</span><span class="sxs-lookup"><span data-stu-id="54b9c-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
