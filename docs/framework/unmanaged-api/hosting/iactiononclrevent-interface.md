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
ms.openlocfilehash: 24191e93d0d8b27d01a914cae76c9ff4e0a7182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430778"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="b8cf9-102">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="b8cf9-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="b8cf9-103">提供[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法，用於執行所使用的呼叫已註冊的事件回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b8cf9-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8cf9-104">方法</span><span class="sxs-lookup"><span data-stu-id="b8cf9-104">Methods</span></span>  
  
|<span data-ttu-id="b8cf9-105">方法</span><span class="sxs-lookup"><span data-stu-id="b8cf9-105">Method</span></span>|<span data-ttu-id="b8cf9-106">描述</span><span class="sxs-lookup"><span data-stu-id="b8cf9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8cf9-107">OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b8cf9-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="b8cf9-108">執行已註冊的事件回呼。</span><span class="sxs-lookup"><span data-stu-id="b8cf9-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8cf9-109">需求</span><span class="sxs-lookup"><span data-stu-id="b8cf9-109">Requirements</span></span>  
 <span data-ttu-id="b8cf9-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8cf9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8cf9-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8cf9-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8cf9-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b8cf9-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8cf9-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8cf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cf9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8cf9-114">See Also</span></span>  
 [<span data-ttu-id="b8cf9-115">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="b8cf9-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="b8cf9-116">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b8cf9-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b8cf9-117">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="b8cf9-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="b8cf9-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b8cf9-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
