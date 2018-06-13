---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 方法
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ed92cbf5a859b9d5b7b8eddefda3ad34a98f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404046"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="dcc03-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="dcc03-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="dcc03-103">由呼叫[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)以偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="dcc03-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc03-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcc03-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcc03-105">參數</span><span class="sxs-lookup"><span data-stu-id="dcc03-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="dcc03-106">[in]要列舉的記憶體區域的起始位址。</span><span class="sxs-lookup"><span data-stu-id="dcc03-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="dcc03-107">[in]以位元組為單位的記憶體區域大小。</span><span class="sxs-lookup"><span data-stu-id="dcc03-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcc03-108">備註</span><span class="sxs-lookup"><span data-stu-id="dcc03-108">Remarks</span></span>  
 <span data-ttu-id="dcc03-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`方法會呼叫此回呼方法來列舉記憶體區域的每次嘗試之後。</span><span class="sxs-lookup"><span data-stu-id="dcc03-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="dcc03-110">即使這個方法會傳回 HRESULT，指出失敗，仍會繼續列舉型別。</span><span class="sxs-lookup"><span data-stu-id="dcc03-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="dcc03-111">此回呼所報告的區域可能會重複或重疊的區域。</span><span class="sxs-lookup"><span data-stu-id="dcc03-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcc03-112">需求</span><span class="sxs-lookup"><span data-stu-id="dcc03-112">Requirements</span></span>  
 <span data-ttu-id="dcc03-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcc03-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc03-114">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dcc03-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dcc03-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcc03-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcc03-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc03-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcc03-117">See Also</span></span>  
 [<span data-ttu-id="dcc03-118">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dcc03-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
