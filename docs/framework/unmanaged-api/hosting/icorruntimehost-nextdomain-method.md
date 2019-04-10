---
title: ICorRuntimeHost::NextDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c3ff0c91713a6bb7449791bae6a754c43659335
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225270"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="0baf4-102">ICorRuntimeHost::NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0baf4-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="0baf4-103">取得列舉型別中的下一個網域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="0baf4-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0baf4-104">語法</span><span class="sxs-lookup"><span data-stu-id="0baf4-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0baf4-105">參數</span><span class="sxs-lookup"><span data-stu-id="0baf4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0baf4-106">[in]列舉值取得透過呼叫[EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0baf4-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="0baf4-107">[out]介面指標<xref:System._AppDomain?displayProperty=nameWithType>型別，表示下一個網域中的列舉型別或 null，如果沒有更多的定義域存在。</span><span class="sxs-lookup"><span data-stu-id="0baf4-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0baf4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0baf4-108">Return Value</span></span>  
  
|<span data-ttu-id="0baf4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0baf4-109">HRESULT</span></span>|<span data-ttu-id="0baf4-110">描述</span><span class="sxs-lookup"><span data-stu-id="0baf4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0baf4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0baf4-111">S_OK</span></span>|<span data-ttu-id="0baf4-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="0baf4-112">The operation was successful.</span></span>|  
|<span data-ttu-id="0baf4-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0baf4-113">S_FALSE</span></span>|<span data-ttu-id="0baf4-114">作業無法完成，或在列舉中有沒有更多的定義域。</span><span class="sxs-lookup"><span data-stu-id="0baf4-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="0baf4-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0baf4-115">E_FAIL</span></span>|<span data-ttu-id="0baf4-116">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="0baf4-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0baf4-117">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="0baf4-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0baf4-118">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0baf4-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0baf4-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0baf4-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0baf4-120">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0baf4-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0baf4-121">需求</span><span class="sxs-lookup"><span data-stu-id="0baf4-121">Requirements</span></span>  
 <span data-ttu-id="0baf4-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0baf4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0baf4-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0baf4-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0baf4-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0baf4-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0baf4-125">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0baf4-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0baf4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0baf4-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0baf4-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="0baf4-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
