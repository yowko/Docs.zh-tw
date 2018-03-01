---
title: "ICLRDataTarget2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8d8dc7aad35e38b2f9d3b5fb48dacbe1d22bd34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="887bc-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="887bc-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="887bc-103">子類別[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)資料存取服務層用來管理目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="887bc-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="887bc-104">方法</span><span class="sxs-lookup"><span data-stu-id="887bc-104">Methods</span></span>  
  
|<span data-ttu-id="887bc-105">方法</span><span class="sxs-lookup"><span data-stu-id="887bc-105">Method</span></span>|<span data-ttu-id="887bc-106">描述</span><span class="sxs-lookup"><span data-stu-id="887bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="887bc-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="887bc-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="887bc-108">配置記憶體中目標處理序的位址空間。</span><span class="sxs-lookup"><span data-stu-id="887bc-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="887bc-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="887bc-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="887bc-110">釋放先前在目標處理序的位址空間配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="887bc-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="887bc-111">備註</span><span class="sxs-lookup"><span data-stu-id="887bc-111">Remarks</span></span>  
 <span data-ttu-id="887bc-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="887bc-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="887bc-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="887bc-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="887bc-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="887bc-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887bc-115">需求</span><span class="sxs-lookup"><span data-stu-id="887bc-115">Requirements</span></span>  
 <span data-ttu-id="887bc-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="887bc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887bc-117">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="887bc-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="887bc-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="887bc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="887bc-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887bc-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="887bc-120">See Also</span></span>  
 [<span data-ttu-id="887bc-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="887bc-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="887bc-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="887bc-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
