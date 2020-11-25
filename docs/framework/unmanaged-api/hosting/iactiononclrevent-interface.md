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
ms.openlocfilehash: 8ca4bb1fe35451f95f752a4e71f5f0b541b55e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721773"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="cce00-102">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="cce00-102">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="cce00-103">提供 [IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md) 方法，該方法會在已使用 [ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 方法呼叫註冊的事件上執行回呼。</span><span class="sxs-lookup"><span data-stu-id="cce00-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cce00-104">方法</span><span class="sxs-lookup"><span data-stu-id="cce00-104">Methods</span></span>  
  
|<span data-ttu-id="cce00-105">方法</span><span class="sxs-lookup"><span data-stu-id="cce00-105">Method</span></span>|<span data-ttu-id="cce00-106">描述</span><span class="sxs-lookup"><span data-stu-id="cce00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cce00-107">OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="cce00-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="cce00-108">針對已註冊的事件執行回呼。</span><span class="sxs-lookup"><span data-stu-id="cce00-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cce00-109">需求</span><span class="sxs-lookup"><span data-stu-id="cce00-109">Requirements</span></span>  

 <span data-ttu-id="cce00-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cce00-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce00-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cce00-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cce00-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="cce00-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cce00-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce00-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cce00-114">See also</span></span>

- [<span data-ttu-id="cce00-115">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="cce00-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="cce00-116">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="cce00-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="cce00-117">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="cce00-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="cce00-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="cce00-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
