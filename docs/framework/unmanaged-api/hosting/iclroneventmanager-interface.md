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
ms.openlocfilehash: 3633db69877db771d919c9f43da4809f8321f77c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951204"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="7a6db-102">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="7a6db-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="7a6db-103">提供的方法可讓主機註冊和取消註冊 common language runtime (CLR) 事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="7a6db-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a6db-104">方法</span><span class="sxs-lookup"><span data-stu-id="7a6db-104">Methods</span></span>  
  
|<span data-ttu-id="7a6db-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a6db-105">Method</span></span>|<span data-ttu-id="7a6db-106">描述</span><span class="sxs-lookup"><span data-stu-id="7a6db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a6db-107">RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="7a6db-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="7a6db-108">為指定的事件註冊回呼指標。</span><span class="sxs-lookup"><span data-stu-id="7a6db-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="7a6db-109">UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="7a6db-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="7a6db-110">將先前註冊的回呼指標取消註冊到指定的事件。</span><span class="sxs-lookup"><span data-stu-id="7a6db-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a6db-111">備註</span><span class="sxs-lookup"><span data-stu-id="7a6db-111">Remarks</span></span>  
 <span data-ttu-id="7a6db-112">若要註冊和取消註冊事件回呼, 主機會藉由`ICLROnEventManager`呼叫[ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法來取得的參考。</span><span class="sxs-lookup"><span data-stu-id="7a6db-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a6db-113">[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)所描述的事件可以從不同的執行緒引發一次以上, 以指示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="7a6db-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a6db-114">需求</span><span class="sxs-lookup"><span data-stu-id="7a6db-114">Requirements</span></span>  
 <span data-ttu-id="7a6db-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a6db-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a6db-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a6db-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a6db-117">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7a6db-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a6db-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a6db-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6db-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a6db-119">See also</span></span>

- [<span data-ttu-id="7a6db-120">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="7a6db-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="7a6db-121">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="7a6db-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="7a6db-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="7a6db-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7a6db-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7a6db-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
