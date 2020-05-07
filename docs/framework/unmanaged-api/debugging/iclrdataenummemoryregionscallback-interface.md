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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860657"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="543d8-102">ICLRDataEnumMemoryRegionsCallback 介面</span><span class="sxs-lookup"><span data-stu-id="543d8-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="543d8-103">提供[ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)的回呼方法，向偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="543d8-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="543d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="543d8-104">Methods</span></span>  
  
|<span data-ttu-id="543d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="543d8-105">Method</span></span>|<span data-ttu-id="543d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="543d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="543d8-107">EnumMemoryRegion 方法</span><span class="sxs-lookup"><span data-stu-id="543d8-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="543d8-108">由`ICLRDataEnumMemoryRegions::EnumMemoryRegions`呼叫以向偵錯工具報告嘗試列舉指定的記憶體區域的結果。</span><span class="sxs-lookup"><span data-stu-id="543d8-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="543d8-109">需求</span><span class="sxs-lookup"><span data-stu-id="543d8-109">Requirements</span></span>  
 <span data-ttu-id="543d8-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="543d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543d8-111">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="543d8-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="543d8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="543d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="543d8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543d8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="543d8-114">See also</span></span>

- [<span data-ttu-id="543d8-115">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="543d8-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
