---
title: ICLRErrorReportingManager::EndCustomDump 方法
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 704d8d0921e671e4172fa6e0ae3f14c4908f289a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615653"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="33418-102">ICLRErrorReportingManager::EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="33418-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="33418-103">移除先前呼叫[ICLRErrorReportingManager：： BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md)方法所指定的自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="33418-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33418-104">語法</span><span class="sxs-lookup"><span data-stu-id="33418-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="33418-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="33418-105">Return Value</span></span>  
  
|<span data-ttu-id="33418-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33418-106">HRESULT</span></span>|<span data-ttu-id="33418-107">說明</span><span class="sxs-lookup"><span data-stu-id="33418-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33418-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="33418-108">S_OK</span></span>|<span data-ttu-id="33418-109">`EndCustomDump`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="33418-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="33418-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33418-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33418-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="33418-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33418-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33418-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33418-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="33418-113">The call timed out.</span></span>|  
|<span data-ttu-id="33418-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33418-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33418-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="33418-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33418-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33418-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33418-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="33418-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33418-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33418-118">E_FAIL</span></span>|<span data-ttu-id="33418-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="33418-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33418-120">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="33418-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33418-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="33418-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33418-122">備註</span><span class="sxs-lookup"><span data-stu-id="33418-122">Remarks</span></span>  
 <span data-ttu-id="33418-123">`EndCustomDump`方法會清除先前呼叫方法所設定的自訂堆疊傾印設定 `BeginCustomDump` ，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="33418-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="33418-124">這應該在自訂堆疊傾印完成後呼叫。</span><span class="sxs-lookup"><span data-stu-id="33418-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33418-125">呼叫失敗 `EndCustomDump` 會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="33418-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33418-126">需求</span><span class="sxs-lookup"><span data-stu-id="33418-126">Requirements</span></span>  
 <span data-ttu-id="33418-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33418-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33418-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="33418-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33418-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="33418-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33418-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33418-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33418-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33418-131">See also</span></span>

- [<span data-ttu-id="33418-132">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="33418-132">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="33418-133">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="33418-133">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="33418-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="33418-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
