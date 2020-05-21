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
ms.openlocfilehash: a97471e1c257902633b7eb363c3cc51288c70917
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762249"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="a5ce2-102">ICorRuntimeHost::EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="a5ce2-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="a5ce2-103">取得目前進程中之定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ce2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5ce2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5ce2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5ce2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a5ce2-106">脫銷定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5ce2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5ce2-107">Return Value</span></span>  
  
|<span data-ttu-id="a5ce2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5ce2-108">HRESULT</span></span>|<span data-ttu-id="a5ce2-109">Description</span><span class="sxs-lookup"><span data-stu-id="a5ce2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5ce2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5ce2-110">S_OK</span></span>|<span data-ttu-id="a5ce2-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-111">The operation was successful.</span></span>|  
|<span data-ttu-id="a5ce2-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a5ce2-112">S_FALSE</span></span>|<span data-ttu-id="a5ce2-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a5ce2-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5ce2-114">E_FAIL</span></span>|<span data-ttu-id="a5ce2-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a5ce2-116">如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a5ce2-117">後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a5ce2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5ce2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5ce2-119">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5ce2-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="a5ce2-120">Requirements</span></span>  
 <span data-ttu-id="a5ce2-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5ce2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ce2-122">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a5ce2-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5ce2-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a5ce2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5ce2-124">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="a5ce2-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ce2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5ce2-125">See also</span></span>

- [<span data-ttu-id="a5ce2-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a5ce2-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
