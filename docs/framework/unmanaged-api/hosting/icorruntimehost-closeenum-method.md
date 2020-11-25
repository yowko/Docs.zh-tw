---
title: ICorRuntimeHost::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: d3748621474373fee8248496d48414ff67c699d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715690"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="cf41f-102">ICorRuntimeHost::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="cf41f-102">ICorRuntimeHost::CloseEnum Method</span></span>

<span data-ttu-id="cf41f-103">將網域列舉值重設回定義域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="cf41f-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf41f-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf41f-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf41f-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf41f-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="cf41f-106">在要重設的列舉值。</span><span class="sxs-lookup"><span data-stu-id="cf41f-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf41f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf41f-107">Return Value</span></span>  
  
|<span data-ttu-id="cf41f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf41f-108">HRESULT</span></span>|<span data-ttu-id="cf41f-109">描述</span><span class="sxs-lookup"><span data-stu-id="cf41f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf41f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf41f-110">S_OK</span></span>|<span data-ttu-id="cf41f-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="cf41f-111">The operation was successful.</span></span>|  
|<span data-ttu-id="cf41f-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cf41f-112">S_FALSE</span></span>|<span data-ttu-id="cf41f-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="cf41f-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cf41f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf41f-114">E_FAIL</span></span>|<span data-ttu-id="cf41f-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="cf41f-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cf41f-116">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="cf41f-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cf41f-117">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cf41f-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cf41f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf41f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf41f-119">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="cf41f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf41f-120">需求</span><span class="sxs-lookup"><span data-stu-id="cf41f-120">Requirements</span></span>  

 <span data-ttu-id="cf41f-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf41f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf41f-122">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cf41f-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf41f-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="cf41f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf41f-124">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="cf41f-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf41f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf41f-125">See also</span></span>

- [<span data-ttu-id="cf41f-126">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="cf41f-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="cf41f-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="cf41f-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
