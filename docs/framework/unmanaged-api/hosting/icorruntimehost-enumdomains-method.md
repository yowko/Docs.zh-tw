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
ms.openlocfilehash: f4338429dc24bf5196b92d3f18e73c98442f61e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720658"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="f7515-102">ICorRuntimeHost::EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="f7515-102">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="f7515-103">取得目前進程中之定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f7515-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7515-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7515-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7515-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7515-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="f7515-106">擴展網域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f7515-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7515-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7515-107">Return Value</span></span>  
  
|<span data-ttu-id="f7515-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7515-108">HRESULT</span></span>|<span data-ttu-id="f7515-109">描述</span><span class="sxs-lookup"><span data-stu-id="f7515-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7515-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7515-110">S_OK</span></span>|<span data-ttu-id="f7515-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="f7515-111">The operation was successful.</span></span>|  
|<span data-ttu-id="f7515-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f7515-112">S_FALSE</span></span>|<span data-ttu-id="f7515-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="f7515-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="f7515-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7515-114">E_FAIL</span></span>|<span data-ttu-id="f7515-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f7515-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f7515-116">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f7515-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f7515-117">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f7515-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f7515-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7515-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7515-119">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f7515-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7515-120">需求</span><span class="sxs-lookup"><span data-stu-id="f7515-120">Requirements</span></span>  

 <span data-ttu-id="f7515-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7515-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7515-122">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f7515-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7515-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f7515-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7515-124">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="f7515-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7515-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7515-125">See also</span></span>

- [<span data-ttu-id="f7515-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f7515-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
