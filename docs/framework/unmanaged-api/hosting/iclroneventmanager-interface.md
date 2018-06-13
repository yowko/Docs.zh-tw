---
title: ICLROnEventManager 介面
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22dfa99d8069c060a525a9ae2cbef73d6625898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434099"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="8c77a-102">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="8c77a-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="8c77a-103">提供方法，讓主應用程式註冊及取消註冊回呼的 common language runtime (CLR) 事件。</span><span class="sxs-lookup"><span data-stu-id="8c77a-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c77a-104">方法</span><span class="sxs-lookup"><span data-stu-id="8c77a-104">Methods</span></span>  
  
|<span data-ttu-id="8c77a-105">方法</span><span class="sxs-lookup"><span data-stu-id="8c77a-105">Method</span></span>|<span data-ttu-id="8c77a-106">描述</span><span class="sxs-lookup"><span data-stu-id="8c77a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c77a-107">RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="8c77a-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="8c77a-108">註冊指定的事件的回呼指標。</span><span class="sxs-lookup"><span data-stu-id="8c77a-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="8c77a-109">UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="8c77a-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="8c77a-110">取消註冊先前註冊的回呼指標為指定的事件。</span><span class="sxs-lookup"><span data-stu-id="8c77a-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c77a-111">備註</span><span class="sxs-lookup"><span data-stu-id="8c77a-111">Remarks</span></span>  
 <span data-ttu-id="8c77a-112">若要註冊和取消註冊事件回呼，主機會取得參考`ICLROnEventManager`藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8c77a-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c77a-113">所描述的事件[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)可以引發一次以上，從不同的執行緒，以便通知卸載或 CLR 的停用。</span><span class="sxs-lookup"><span data-stu-id="8c77a-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c77a-114">需求</span><span class="sxs-lookup"><span data-stu-id="8c77a-114">Requirements</span></span>  
 <span data-ttu-id="8c77a-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c77a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c77a-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c77a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c77a-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8c77a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c77a-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c77a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c77a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c77a-119">See Also</span></span>  
 [<span data-ttu-id="8c77a-120">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="8c77a-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="8c77a-121">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="8c77a-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="8c77a-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8c77a-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8c77a-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="8c77a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
