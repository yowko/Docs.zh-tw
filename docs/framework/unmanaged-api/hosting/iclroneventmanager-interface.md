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
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140850"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="b3690-102">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3690-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="b3690-103">提供的方法可讓主機註冊和取消註冊 common language runtime （CLR）事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="b3690-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3690-104">方法</span><span class="sxs-lookup"><span data-stu-id="b3690-104">Methods</span></span>  
  
|<span data-ttu-id="b3690-105">方法</span><span class="sxs-lookup"><span data-stu-id="b3690-105">Method</span></span>|<span data-ttu-id="b3690-106">描述</span><span class="sxs-lookup"><span data-stu-id="b3690-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3690-107">RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b3690-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="b3690-108">為指定的事件註冊回呼指標。</span><span class="sxs-lookup"><span data-stu-id="b3690-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="b3690-109">UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b3690-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="b3690-110">將先前註冊的回呼指標取消註冊到指定的事件。</span><span class="sxs-lookup"><span data-stu-id="b3690-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3690-111">備註</span><span class="sxs-lookup"><span data-stu-id="b3690-111">Remarks</span></span>  
 <span data-ttu-id="b3690-112">若要註冊和取消註冊事件回呼，主機會藉由呼叫[ICLRControl：： GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法來取得 `ICLROnEventManager` 的參考。</span><span class="sxs-lookup"><span data-stu-id="b3690-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3690-113">[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)所描述的事件可以從不同的執行緒引發一次以上，以指示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="b3690-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3690-114">需求</span><span class="sxs-lookup"><span data-stu-id="b3690-114">Requirements</span></span>  
 <span data-ttu-id="b3690-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3690-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3690-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b3690-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3690-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3690-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3690-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3690-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3690-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3690-119">See also</span></span>

- [<span data-ttu-id="b3690-120">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="b3690-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="b3690-121">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="b3690-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="b3690-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b3690-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b3690-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b3690-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
