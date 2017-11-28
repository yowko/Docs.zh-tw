---
title: "ICLRDebugManager::SetSymbolReadingPolicy 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d116883c39b4400451ede07df83ac77893ce285c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="0ac8f-102">ICLRDebugManager::SetSymbolReadingPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="0ac8f-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="0ac8f-103">設定用於讀取程式資料庫 (PDB) 檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="0ac8f-104">原則會決定是否在呼叫堆疊中包含行號和檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac8f-105">語法</span><span class="sxs-lookup"><span data-stu-id="0ac8f-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ac8f-106">參數</span><span class="sxs-lookup"><span data-stu-id="0ac8f-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="0ac8f-107">[in]成員[ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ac8f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ac8f-108">Return Value</span></span>  
  
|<span data-ttu-id="0ac8f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ac8f-109">HRESULT</span></span>|<span data-ttu-id="0ac8f-110">描述</span><span class="sxs-lookup"><span data-stu-id="0ac8f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ac8f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ac8f-111">S_OK</span></span>|<span data-ttu-id="0ac8f-112">`SetSymbolReadingPolicy`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="0ac8f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ac8f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ac8f-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ac8f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ac8f-115">E_FAIL</span></span>|<span data-ttu-id="0ac8f-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ac8f-117">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ac8f-118">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ac8f-119">需求</span><span class="sxs-lookup"><span data-stu-id="0ac8f-119">Requirements</span></span>  
 <span data-ttu-id="0ac8f-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ac8f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ac8f-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ac8f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ac8f-122">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ac8f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ac8f-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ac8f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac8f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ac8f-124">See Also</span></span>  
 [<span data-ttu-id="0ac8f-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ac8f-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
