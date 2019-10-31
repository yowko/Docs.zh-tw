---
title: IActionOnCLREvent 介面
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9277fe2c241ce4f502339de826dccd08a2ce8055
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126963"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="169ba-102">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="169ba-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="169ba-103">提供[IActionOnCLREvent：： OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法，它會在使用[ICLROnEventManager：： RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法呼叫註冊的事件上執行回呼。</span><span class="sxs-lookup"><span data-stu-id="169ba-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="169ba-104">方法</span><span class="sxs-lookup"><span data-stu-id="169ba-104">Methods</span></span>  
  
|<span data-ttu-id="169ba-105">方法</span><span class="sxs-lookup"><span data-stu-id="169ba-105">Method</span></span>|<span data-ttu-id="169ba-106">描述</span><span class="sxs-lookup"><span data-stu-id="169ba-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="169ba-107">OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="169ba-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="169ba-108">針對已註冊的事件執行回呼。</span><span class="sxs-lookup"><span data-stu-id="169ba-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="169ba-109">需求</span><span class="sxs-lookup"><span data-stu-id="169ba-109">Requirements</span></span>  
 <span data-ttu-id="169ba-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="169ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169ba-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="169ba-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="169ba-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="169ba-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="169ba-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169ba-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="169ba-114">See also</span></span>

- [<span data-ttu-id="169ba-115">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="169ba-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="169ba-116">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="169ba-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="169ba-117">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="169ba-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="169ba-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="169ba-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
