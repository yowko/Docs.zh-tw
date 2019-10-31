---
title: ICorRuntimeHost::CreateDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 7c3e37fdb8a5afc973c913b1cfa56ab2e9f4fa52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127723"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="7390f-102">ICorRuntimeHost::CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="7390f-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="7390f-103">建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7390f-103">Creates an application domain.</span></span> <span data-ttu-id="7390f-104">呼叫端會接收類型的介面指標，<xref:System._AppDomain> 類型 <xref:System.AppDomain?displayProperty=nameWithType>的實例。</span><span class="sxs-lookup"><span data-stu-id="7390f-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7390f-105">語法</span><span class="sxs-lookup"><span data-stu-id="7390f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7390f-106">參數</span><span class="sxs-lookup"><span data-stu-id="7390f-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="7390f-107">在選擇性參數，用來為定義域提供易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7390f-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="7390f-108">這個易記名稱可以在使用者介面（例如偵錯工具）中顯示，以識別網域。</span><span class="sxs-lookup"><span data-stu-id="7390f-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="7390f-109">在指向 `IIdentity` 實例的選擇性陣列，表示透過安全性原則對應的辨識項，以建立許可權集合。</span><span class="sxs-lookup"><span data-stu-id="7390f-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="7390f-110">您可以藉由呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法來取得 `IIdentity` 物件。</span><span class="sxs-lookup"><span data-stu-id="7390f-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="7390f-111">脫銷類型的介面指標 <xref:System._AppDomain> 至可用來進一步控制定義域的 <xref:System.AppDomain?displayProperty=nameWithType> 實例。</span><span class="sxs-lookup"><span data-stu-id="7390f-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7390f-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7390f-112">Return Value</span></span>  
  
|<span data-ttu-id="7390f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7390f-113">HRESULT</span></span>|<span data-ttu-id="7390f-114">描述</span><span class="sxs-lookup"><span data-stu-id="7390f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7390f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7390f-115">S_OK</span></span>|<span data-ttu-id="7390f-116">作業成功。</span><span class="sxs-lookup"><span data-stu-id="7390f-116">The operation was successful.</span></span>|  
|<span data-ttu-id="7390f-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7390f-117">S_FALSE</span></span>|<span data-ttu-id="7390f-118">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="7390f-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7390f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7390f-119">E_FAIL</span></span>|<span data-ttu-id="7390f-120">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7390f-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7390f-121">如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。</span><span class="sxs-lookup"><span data-stu-id="7390f-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7390f-122">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7390f-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7390f-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7390f-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7390f-124">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7390f-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7390f-125">需求</span><span class="sxs-lookup"><span data-stu-id="7390f-125">Requirements</span></span>  
 <span data-ttu-id="7390f-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7390f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7390f-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7390f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7390f-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7390f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7390f-129">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="7390f-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7390f-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="7390f-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="7390f-131">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="7390f-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
