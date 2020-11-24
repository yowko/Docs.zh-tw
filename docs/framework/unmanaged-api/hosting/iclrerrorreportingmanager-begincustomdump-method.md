---
title: ICLRErrorReportingManager::BeginCustomDump 方法
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 199c130d70cfbf0d383c2e0dc148ffe3dc1242d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673552"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="1aa51-102">ICLRErrorReportingManager::BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="1aa51-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="1aa51-103">針對錯誤報表，指定自訂堆積傾印的設定。</span><span class="sxs-lookup"><span data-stu-id="1aa51-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa51-104">語法</span><span class="sxs-lookup"><span data-stu-id="1aa51-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aa51-105">參數</span><span class="sxs-lookup"><span data-stu-id="1aa51-105">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="1aa51-106">在 [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) 值，指出要在其上建立自訂堆積傾印的堆積傾印類型。</span><span class="sxs-lookup"><span data-stu-id="1aa51-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="1aa51-107">在陣列的長度 `items` 。</span><span class="sxs-lookup"><span data-stu-id="1aa51-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="1aa51-108">如果 `dwFlavor` 不是 DUMP_FLAVOR_Mini，則 `dwNumItems` 應為零。</span><span class="sxs-lookup"><span data-stu-id="1aa51-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="1aa51-109">在 [CustomDumpItem](customdumpitem-structure.md) 實例的陣列，指定要新增至迷你傾印的專案。</span><span class="sxs-lookup"><span data-stu-id="1aa51-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="1aa51-110">如果 `dwFlavor` 不是 DUMP_FLAVOR_Mini，則 `items` 應該是 null。</span><span class="sxs-lookup"><span data-stu-id="1aa51-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="1aa51-111">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="1aa51-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aa51-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="1aa51-112">Return Value</span></span>  
  
|<span data-ttu-id="1aa51-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1aa51-113">HRESULT</span></span>|<span data-ttu-id="1aa51-114">描述</span><span class="sxs-lookup"><span data-stu-id="1aa51-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1aa51-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1aa51-115">S_OK</span></span>|<span data-ttu-id="1aa51-116">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1aa51-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="1aa51-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1aa51-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1aa51-118">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1aa51-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1aa51-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1aa51-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1aa51-120">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="1aa51-120">The call timed out.</span></span>|  
|<span data-ttu-id="1aa51-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1aa51-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1aa51-122">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1aa51-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1aa51-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1aa51-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1aa51-124">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="1aa51-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1aa51-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1aa51-125">E_FAIL</span></span>|<span data-ttu-id="1aa51-126">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1aa51-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1aa51-127">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="1aa51-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1aa51-128">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1aa51-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aa51-129">備註</span><span class="sxs-lookup"><span data-stu-id="1aa51-129">Remarks</span></span>  

 <span data-ttu-id="1aa51-130">`BeginCustomDump`方法會設定自訂堆積傾印設定。</span><span class="sxs-lookup"><span data-stu-id="1aa51-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="1aa51-131">[EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md)方法會清除自訂堆積傾印設定，並釋出任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="1aa51-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="1aa51-132">它應該在自訂堆積傾印完成之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="1aa51-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1aa51-133">呼叫失敗 `EndCustomDump` 會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="1aa51-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa51-134">需求</span><span class="sxs-lookup"><span data-stu-id="1aa51-134">Requirements</span></span>  

 <span data-ttu-id="1aa51-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa51-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa51-136">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1aa51-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1aa51-137">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1aa51-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1aa51-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa51-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa51-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aa51-139">See also</span></span>

- [<span data-ttu-id="1aa51-140">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="1aa51-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="1aa51-141">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="1aa51-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="1aa51-142">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="1aa51-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
