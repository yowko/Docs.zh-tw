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
ms.openlocfilehash: 1f0f4331302e56a90b4aefd657e07981994022ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112305"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="70c54-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="70c54-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="70c54-103">資料存取服務層用來操作目標進程中虛擬記憶體區域的[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)子類別。</span><span class="sxs-lookup"><span data-stu-id="70c54-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70c54-104">方法</span><span class="sxs-lookup"><span data-stu-id="70c54-104">Methods</span></span>  
  
|<span data-ttu-id="70c54-105">方法</span><span class="sxs-lookup"><span data-stu-id="70c54-105">Method</span></span>|<span data-ttu-id="70c54-106">描述</span><span class="sxs-lookup"><span data-stu-id="70c54-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70c54-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="70c54-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="70c54-108">在目標進程的位址空間中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="70c54-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="70c54-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="70c54-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="70c54-110">釋放先前在目標進程的位址空間中配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="70c54-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c54-111">備註</span><span class="sxs-lookup"><span data-stu-id="70c54-111">Remarks</span></span>  
 <span data-ttu-id="70c54-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="70c54-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="70c54-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="70c54-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="70c54-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="70c54-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c54-115">需求</span><span class="sxs-lookup"><span data-stu-id="70c54-115">Requirements</span></span>  
 <span data-ttu-id="70c54-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70c54-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c54-117">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="70c54-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="70c54-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70c54-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70c54-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c54-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c54-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="70c54-120">See also</span></span>

- [<span data-ttu-id="70c54-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="70c54-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="70c54-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70c54-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
