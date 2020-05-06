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
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860696"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="a0150-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法</span><span class="sxs-lookup"><span data-stu-id="a0150-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="a0150-103">列舉指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="a0150-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0150-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0150-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0150-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0150-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="a0150-106">在[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)實例的指標，此方法會針對每個列舉的記憶體區域呼叫，以通知偵錯工具結果。</span><span class="sxs-lookup"><span data-stu-id="a0150-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="a0150-107">即使回呼表示失敗，記憶體區域的列舉仍會繼續。</span><span class="sxs-lookup"><span data-stu-id="a0150-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="a0150-108">在未使用。</span><span class="sxs-lookup"><span data-stu-id="a0150-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="a0150-109">在[CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md)列舉的值，指定要列舉的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="a0150-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0150-110">備註</span><span class="sxs-lookup"><span data-stu-id="a0150-110">Remarks</span></span>  
 <span data-ttu-id="a0150-111">這個方法會使用指定的[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)實例來通知呼叫者結果。</span><span class="sxs-lookup"><span data-stu-id="a0150-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0150-112">需求</span><span class="sxs-lookup"><span data-stu-id="a0150-112">Requirements</span></span>  
 <span data-ttu-id="a0150-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0150-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0150-114">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="a0150-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a0150-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0150-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0150-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0150-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0150-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0150-117">See also</span></span>

- [<span data-ttu-id="a0150-118">ICLRDataEnumMemoryRegions 介面</span><span class="sxs-lookup"><span data-stu-id="a0150-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
