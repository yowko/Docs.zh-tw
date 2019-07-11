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
ms.openlocfilehash: 4ac86fdc0852c701b66986b6a304695fbdc8e755
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780390"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="dc639-102">ICorRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="dc639-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="dc639-103">啟動 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="dc639-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc639-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc639-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dc639-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="dc639-105">Return Value</span></span>  
  
|<span data-ttu-id="dc639-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc639-106">HRESULT</span></span>|<span data-ttu-id="dc639-107">說明</span><span class="sxs-lookup"><span data-stu-id="dc639-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc639-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc639-108">S_OK</span></span>|<span data-ttu-id="dc639-109">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="dc639-109">The operation was successful.</span></span>|  
|<span data-ttu-id="dc639-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dc639-110">S_FALSE</span></span>|<span data-ttu-id="dc639-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="dc639-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="dc639-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc639-112">E_FAIL</span></span>|<span data-ttu-id="dc639-113">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="dc639-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dc639-114">如果方法會傳回 E_FAIL，CLR 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="dc639-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="dc639-115">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dc639-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dc639-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc639-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc639-117">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dc639-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc639-118">備註</span><span class="sxs-lookup"><span data-stu-id="dc639-118">Remarks</span></span>  
 <span data-ttu-id="dc639-119">它通常是不需要呼叫`Start`方法，因為 CLR 會自動啟動時執行 managed 程式碼的第一個要求。</span><span class="sxs-lookup"><span data-stu-id="dc639-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc639-120">需求</span><span class="sxs-lookup"><span data-stu-id="dc639-120">Requirements</span></span>  
 <span data-ttu-id="dc639-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc639-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc639-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc639-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc639-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dc639-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc639-124">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="dc639-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc639-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc639-125">See also</span></span>

- [<span data-ttu-id="dc639-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="dc639-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
