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
ms.openlocfilehash: e5a1642f968228c5815732ecd470cb8f02a0eb83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139578"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="b454f-102">ICorRuntimeHost::EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="b454f-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="b454f-103">取得目前進程中之定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b454f-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b454f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b454f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b454f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b454f-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b454f-106">脫銷定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b454f-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b454f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b454f-107">Return Value</span></span>  
  
|<span data-ttu-id="b454f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b454f-108">HRESULT</span></span>|<span data-ttu-id="b454f-109">描述</span><span class="sxs-lookup"><span data-stu-id="b454f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b454f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b454f-110">S_OK</span></span>|<span data-ttu-id="b454f-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="b454f-111">The operation was successful.</span></span>|  
|<span data-ttu-id="b454f-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b454f-112">S_FALSE</span></span>|<span data-ttu-id="b454f-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="b454f-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b454f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b454f-114">E_FAIL</span></span>|<span data-ttu-id="b454f-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b454f-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b454f-116">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="b454f-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b454f-117">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b454f-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b454f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b454f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b454f-119">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b454f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b454f-120">需求</span><span class="sxs-lookup"><span data-stu-id="b454f-120">Requirements</span></span>  
 <span data-ttu-id="b454f-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b454f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b454f-122">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b454f-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b454f-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b454f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b454f-124">**.NET Framework 版本：** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="b454f-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b454f-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="b454f-125">See also</span></span>

- [<span data-ttu-id="b454f-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b454f-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
