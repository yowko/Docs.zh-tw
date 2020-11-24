---
title: ICorRuntimeHost::UnloadDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: 94c84d876e19ec2ff7baba5a5a7420eec68d58c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690105"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="be45c-102">ICorRuntimeHost::UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="be45c-102">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="be45c-103">從目前的進程卸載指定的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="be45c-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be45c-104">語法</span><span class="sxs-lookup"><span data-stu-id="be45c-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be45c-105">參數</span><span class="sxs-lookup"><span data-stu-id="be45c-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="be45c-106">在代表要卸載之網域的型別指標 <xref:System._AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="be45c-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be45c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="be45c-107">Return Value</span></span>  
  
|<span data-ttu-id="be45c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be45c-108">HRESULT</span></span>|<span data-ttu-id="be45c-109">描述</span><span class="sxs-lookup"><span data-stu-id="be45c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be45c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="be45c-110">S_OK</span></span>|<span data-ttu-id="be45c-111">作業成功。</span><span class="sxs-lookup"><span data-stu-id="be45c-111">The operation was successful.</span></span>|  
|<span data-ttu-id="be45c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="be45c-112">S_FALSE</span></span>|<span data-ttu-id="be45c-113">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="be45c-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="be45c-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be45c-114">E_FAIL</span></span>|<span data-ttu-id="be45c-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="be45c-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="be45c-116">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="be45c-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="be45c-117">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="be45c-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be45c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be45c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be45c-119">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="be45c-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be45c-120">需求</span><span class="sxs-lookup"><span data-stu-id="be45c-120">Requirements</span></span>  

 <span data-ttu-id="be45c-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be45c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be45c-122">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="be45c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be45c-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="be45c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be45c-124">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="be45c-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be45c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be45c-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="be45c-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="be45c-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
