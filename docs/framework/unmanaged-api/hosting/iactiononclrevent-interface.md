---
title: "IActionOnCLREvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent
helpviewer_keywords: IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eecc04fea993de3c502d1a203f0023c81c3b7909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="fa2ee-102">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="fa2ee-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="fa2ee-103">提供[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法，用於執行所使用的呼叫已註冊的事件回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fa2ee-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa2ee-104">方法</span><span class="sxs-lookup"><span data-stu-id="fa2ee-104">Methods</span></span>  
  
|<span data-ttu-id="fa2ee-105">方法</span><span class="sxs-lookup"><span data-stu-id="fa2ee-105">Method</span></span>|<span data-ttu-id="fa2ee-106">說明</span><span class="sxs-lookup"><span data-stu-id="fa2ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa2ee-107">OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="fa2ee-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="fa2ee-108">執行已註冊的事件回呼。</span><span class="sxs-lookup"><span data-stu-id="fa2ee-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa2ee-109">需求</span><span class="sxs-lookup"><span data-stu-id="fa2ee-109">Requirements</span></span>  
 <span data-ttu-id="fa2ee-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa2ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa2ee-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa2ee-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa2ee-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fa2ee-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa2ee-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa2ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2ee-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa2ee-114">See Also</span></span>  
 [<span data-ttu-id="fa2ee-115">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="fa2ee-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="fa2ee-116">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="fa2ee-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fa2ee-117">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="fa2ee-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="fa2ee-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fa2ee-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
