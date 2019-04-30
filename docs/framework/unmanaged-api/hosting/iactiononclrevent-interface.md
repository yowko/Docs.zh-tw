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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985526"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="3bb1a-102">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="3bb1a-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="3bb1a-103">提供[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法，對事件所使用的呼叫已註冊的回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3bb1a-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bb1a-104">方法</span><span class="sxs-lookup"><span data-stu-id="3bb1a-104">Methods</span></span>  
  
|<span data-ttu-id="3bb1a-105">方法</span><span class="sxs-lookup"><span data-stu-id="3bb1a-105">Method</span></span>|<span data-ttu-id="3bb1a-106">描述</span><span class="sxs-lookup"><span data-stu-id="3bb1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bb1a-107">OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="3bb1a-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="3bb1a-108">執行已註冊的事件回呼。</span><span class="sxs-lookup"><span data-stu-id="3bb1a-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bb1a-109">需求</span><span class="sxs-lookup"><span data-stu-id="3bb1a-109">Requirements</span></span>  
 <span data-ttu-id="3bb1a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb1a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb1a-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bb1a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bb1a-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3bb1a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bb1a-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb1a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb1a-114">See also</span></span>

- [<span data-ttu-id="3bb1a-115">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="3bb1a-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="3bb1a-116">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="3bb1a-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3bb1a-117">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="3bb1a-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="3bb1a-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3bb1a-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
