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
ms.openlocfilehash: 6fc26694bded2c7df1a53a96e8743f3be73c93eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408500"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="33207-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="33207-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="33207-103">子類別[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)資料存取服務層用來管理目標處理序中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="33207-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33207-104">方法</span><span class="sxs-lookup"><span data-stu-id="33207-104">Methods</span></span>  
  
|<span data-ttu-id="33207-105">方法</span><span class="sxs-lookup"><span data-stu-id="33207-105">Method</span></span>|<span data-ttu-id="33207-106">描述</span><span class="sxs-lookup"><span data-stu-id="33207-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33207-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="33207-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="33207-108">配置記憶體中目標處理序的位址空間。</span><span class="sxs-lookup"><span data-stu-id="33207-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="33207-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="33207-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="33207-110">釋放先前在目標處理序的位址空間配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="33207-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33207-111">備註</span><span class="sxs-lookup"><span data-stu-id="33207-111">Remarks</span></span>  
 <span data-ttu-id="33207-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="33207-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="33207-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="33207-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="33207-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="33207-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33207-115">需求</span><span class="sxs-lookup"><span data-stu-id="33207-115">Requirements</span></span>  
 <span data-ttu-id="33207-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33207-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33207-117">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="33207-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="33207-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33207-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33207-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33207-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33207-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33207-120">See Also</span></span>  
 [<span data-ttu-id="33207-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="33207-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="33207-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="33207-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
