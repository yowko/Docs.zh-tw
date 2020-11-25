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
ms.openlocfilehash: b5ca524d223fad7ded0d56def3293eb40be69fa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703716"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="345ec-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="345ec-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="345ec-103">由 [ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) 呼叫，以向偵錯工具報告嘗試列舉指定之記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="345ec-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="345ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="345ec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="345ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="345ec-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="345ec-106">在要列舉之記憶體區域的起始位址。</span><span class="sxs-lookup"><span data-stu-id="345ec-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="345ec-107">在記憶體區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="345ec-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="345ec-108">備註</span><span class="sxs-lookup"><span data-stu-id="345ec-108">Remarks</span></span>  

 <span data-ttu-id="345ec-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`方法會在每次嘗試列舉記憶體區域之後，呼叫這個回呼方法。</span><span class="sxs-lookup"><span data-stu-id="345ec-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="345ec-110">即使這個方法會傳回指出失敗的 HRESULT，也會繼續列舉。</span><span class="sxs-lookup"><span data-stu-id="345ec-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="345ec-111">此回呼所報告的區域可能是重複或重迭的區域。</span><span class="sxs-lookup"><span data-stu-id="345ec-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="345ec-112">需求</span><span class="sxs-lookup"><span data-stu-id="345ec-112">Requirements</span></span>  

 <span data-ttu-id="345ec-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="345ec-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="345ec-114">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="345ec-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="345ec-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="345ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="345ec-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="345ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345ec-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345ec-117">See also</span></span>

- [<span data-ttu-id="345ec-118">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="345ec-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
