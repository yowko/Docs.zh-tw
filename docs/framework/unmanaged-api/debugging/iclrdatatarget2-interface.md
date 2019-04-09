---
title: ICLRDataTarget2 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21bced214242866c47f40f392593f3f51cda02f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104711"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="2cc7d-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="2cc7d-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="2cc7d-103">子類別[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)可由資料存取服務層來操作目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cc7d-104">方法</span><span class="sxs-lookup"><span data-stu-id="2cc7d-104">Methods</span></span>  
  
|<span data-ttu-id="2cc7d-105">方法</span><span class="sxs-lookup"><span data-stu-id="2cc7d-105">Method</span></span>|<span data-ttu-id="2cc7d-106">描述</span><span class="sxs-lookup"><span data-stu-id="2cc7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cc7d-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="2cc7d-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="2cc7d-108">配置記憶體中目標處理序的位址空間。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="2cc7d-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="2cc7d-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="2cc7d-110">釋放先前配置的目標處理序的位址空間中的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cc7d-111">備註</span><span class="sxs-lookup"><span data-stu-id="2cc7d-111">Remarks</span></span>  
 <span data-ttu-id="2cc7d-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="2cc7d-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="2cc7d-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cc7d-115">需求</span><span class="sxs-lookup"><span data-stu-id="2cc7d-115">Requirements</span></span>  
 <span data-ttu-id="2cc7d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cc7d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc7d-117">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2cc7d-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2cc7d-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cc7d-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2cc7d-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2cc7d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2cc7d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cc7d-120">See also</span></span>

- [<span data-ttu-id="2cc7d-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="2cc7d-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="2cc7d-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2cc7d-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
