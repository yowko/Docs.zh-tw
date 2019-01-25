---
title: ICLRDebugManager::SetSymbolReadingPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 330501e67e3f19fbdb24c200deacad68de1b6c03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710284"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="6cd4b-102">ICLRDebugManager::SetSymbolReadingPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="6cd4b-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="6cd4b-103">設定用於讀取程式資料庫 (PDB) 檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="6cd4b-104">原則會決定是否在呼叫堆疊中包含行號和檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd4b-105">語法</span><span class="sxs-lookup"><span data-stu-id="6cd4b-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cd4b-106">參數</span><span class="sxs-lookup"><span data-stu-id="6cd4b-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="6cd4b-107">[in]成員[ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cd4b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cd4b-108">Return Value</span></span>  
  
|<span data-ttu-id="6cd4b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cd4b-109">HRESULT</span></span>|<span data-ttu-id="6cd4b-110">描述</span><span class="sxs-lookup"><span data-stu-id="6cd4b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cd4b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cd4b-111">S_OK</span></span>|<span data-ttu-id="6cd4b-112">`SetSymbolReadingPolicy` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="6cd4b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cd4b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cd4b-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cd4b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cd4b-115">E_FAIL</span></span>|<span data-ttu-id="6cd4b-116">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cd4b-117">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cd4b-118">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cd4b-119">需求</span><span class="sxs-lookup"><span data-stu-id="6cd4b-119">Requirements</span></span>  
 <span data-ttu-id="6cd4b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd4b-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cd4b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cd4b-122">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6cd4b-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd4b-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd4b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd4b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cd4b-124">See also</span></span>
- [<span data-ttu-id="6cd4b-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="6cd4b-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
