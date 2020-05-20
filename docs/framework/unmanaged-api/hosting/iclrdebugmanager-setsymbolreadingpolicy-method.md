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
ms.openlocfilehash: f037e902a9f573023022c81503ea3b987cf6d424
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615738"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="77b19-102">ICLRDebugManager::SetSymbolReadingPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="77b19-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="77b19-103">設定用於讀取程式資料庫（PDB）檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="77b19-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="77b19-104">此原則會決定行號和檔案的相關資訊是否包含在呼叫堆疊中。</span><span class="sxs-lookup"><span data-stu-id="77b19-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b19-105">語法</span><span class="sxs-lookup"><span data-stu-id="77b19-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77b19-106">參數</span><span class="sxs-lookup"><span data-stu-id="77b19-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="77b19-107">在[ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md)列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="77b19-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77b19-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="77b19-108">Return Value</span></span>  
  
|<span data-ttu-id="77b19-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77b19-109">HRESULT</span></span>|<span data-ttu-id="77b19-110">說明</span><span class="sxs-lookup"><span data-stu-id="77b19-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77b19-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77b19-111">S_OK</span></span>|<span data-ttu-id="77b19-112">`SetSymbolReadingPolicy`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="77b19-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="77b19-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77b19-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77b19-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="77b19-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77b19-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77b19-115">E_FAIL</span></span>|<span data-ttu-id="77b19-116">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="77b19-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77b19-117">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="77b19-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77b19-118">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="77b19-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77b19-119">需求</span><span class="sxs-lookup"><span data-stu-id="77b19-119">Requirements</span></span>  
 <span data-ttu-id="77b19-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77b19-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b19-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="77b19-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77b19-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="77b19-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77b19-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77b19-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b19-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77b19-124">See also</span></span>

- [<span data-ttu-id="77b19-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="77b19-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
