---
title: ICorRuntimeHost::EnumDomains 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69fcc862e98e305105a6f17ca49940bd10cef39c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072554"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="61ff1-102">ICorRuntimeHost::EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="61ff1-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="61ff1-103">取得目前的處理序中的網域列舉值。</span><span class="sxs-lookup"><span data-stu-id="61ff1-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ff1-104">語法</span><span class="sxs-lookup"><span data-stu-id="61ff1-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ff1-105">參數</span><span class="sxs-lookup"><span data-stu-id="61ff1-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="61ff1-106">[out]網域列舉值。</span><span class="sxs-lookup"><span data-stu-id="61ff1-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61ff1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="61ff1-107">Return Value</span></span>  
  
|<span data-ttu-id="61ff1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61ff1-108">HRESULT</span></span>|<span data-ttu-id="61ff1-109">描述</span><span class="sxs-lookup"><span data-stu-id="61ff1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61ff1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="61ff1-110">S_OK</span></span>|<span data-ttu-id="61ff1-111">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="61ff1-111">The operation was successful.</span></span>|  
|<span data-ttu-id="61ff1-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="61ff1-112">S_FALSE</span></span>|<span data-ttu-id="61ff1-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="61ff1-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="61ff1-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61ff1-114">E_FAIL</span></span>|<span data-ttu-id="61ff1-115">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="61ff1-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="61ff1-116">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="61ff1-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="61ff1-117">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="61ff1-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="61ff1-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61ff1-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61ff1-119">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="61ff1-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61ff1-120">需求</span><span class="sxs-lookup"><span data-stu-id="61ff1-120">Requirements</span></span>  
 <span data-ttu-id="61ff1-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61ff1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ff1-122">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61ff1-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61ff1-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61ff1-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61ff1-124">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="61ff1-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ff1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61ff1-125">See also</span></span>

- [<span data-ttu-id="61ff1-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="61ff1-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
