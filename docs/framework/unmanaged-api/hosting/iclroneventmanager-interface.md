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
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703512"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="01d99-102">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="01d99-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="01d99-103">提供的方法可讓主機註冊和取消註冊 common language runtime （CLR）事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="01d99-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01d99-104">方法</span><span class="sxs-lookup"><span data-stu-id="01d99-104">Methods</span></span>  
  
|<span data-ttu-id="01d99-105">方法</span><span class="sxs-lookup"><span data-stu-id="01d99-105">Method</span></span>|<span data-ttu-id="01d99-106">描述</span><span class="sxs-lookup"><span data-stu-id="01d99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01d99-107">RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="01d99-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="01d99-108">為指定的事件註冊回呼指標。</span><span class="sxs-lookup"><span data-stu-id="01d99-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="01d99-109">UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="01d99-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="01d99-110">將先前註冊的回呼指標取消註冊到指定的事件。</span><span class="sxs-lookup"><span data-stu-id="01d99-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d99-111">備註</span><span class="sxs-lookup"><span data-stu-id="01d99-111">Remarks</span></span>  
 <span data-ttu-id="01d99-112">若要註冊和取消註冊事件回呼，主機會藉 `ICLROnEventManager` 由呼叫[ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md)方法來取得的參考。</span><span class="sxs-lookup"><span data-stu-id="01d99-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d99-113">[EClrEvent](eclrevent-enumeration.md)所描述的事件可以從不同的執行緒引發一次以上，以指示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="01d99-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d99-114">需求</span><span class="sxs-lookup"><span data-stu-id="01d99-114">Requirements</span></span>  
 <span data-ttu-id="01d99-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01d99-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d99-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="01d99-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01d99-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01d99-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01d99-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d99-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d99-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d99-119">See also</span></span>

- [<span data-ttu-id="01d99-120">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="01d99-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="01d99-121">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="01d99-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="01d99-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="01d99-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="01d99-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="01d99-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
