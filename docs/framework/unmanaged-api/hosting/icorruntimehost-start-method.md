---
title: ICorRuntimeHost::Start 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96e8d80e2dff88aa5a589f864278b4a4e9cc76ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437010"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="36235-102">ICorRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="36235-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="36235-103">啟動 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="36235-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36235-104">語法</span><span class="sxs-lookup"><span data-stu-id="36235-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="36235-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="36235-105">Return Value</span></span>  
  
|<span data-ttu-id="36235-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36235-106">HRESULT</span></span>|<span data-ttu-id="36235-107">描述</span><span class="sxs-lookup"><span data-stu-id="36235-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36235-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="36235-108">S_OK</span></span>|<span data-ttu-id="36235-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="36235-109">The operation was successful.</span></span>|  
|<span data-ttu-id="36235-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="36235-110">S_FALSE</span></span>|<span data-ttu-id="36235-111">無法完成操作。</span><span class="sxs-lookup"><span data-stu-id="36235-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="36235-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36235-112">E_FAIL</span></span>|<span data-ttu-id="36235-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="36235-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="36235-114">若方法會傳回 E_FAIL，CLR 就不會再處理序中。</span><span class="sxs-lookup"><span data-stu-id="36235-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="36235-115">任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="36235-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="36235-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36235-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36235-117">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="36235-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36235-118">備註</span><span class="sxs-lookup"><span data-stu-id="36235-118">Remarks</span></span>  
 <span data-ttu-id="36235-119">它通常是不需要呼叫`Start`方法，因為 CLR 執行 managed 程式碼的第一個要求時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="36235-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36235-120">需求</span><span class="sxs-lookup"><span data-stu-id="36235-120">Requirements</span></span>  
 <span data-ttu-id="36235-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36235-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36235-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36235-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36235-123">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="36235-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36235-124">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="36235-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36235-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36235-125">See Also</span></span>  
 [<span data-ttu-id="36235-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="36235-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
