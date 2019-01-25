---
title: ICLRAssemblyIdentityManager::IsStronglyNamed 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a958e38857d2407930cb8c03a08eabdf6574cda9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563882"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="cfeae-102">ICLRAssemblyIdentityManager::IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="cfeae-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="cfeae-103">取得值，指出是否指定的組件強式名稱。</span><span class="sxs-lookup"><span data-stu-id="cfeae-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfeae-104">語法</span><span class="sxs-lookup"><span data-stu-id="cfeae-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfeae-105">參數</span><span class="sxs-lookup"><span data-stu-id="cfeae-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="cfeae-106">[in]要評估的組件不透明的標準組件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="cfeae-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="cfeae-107">[out]`true`，如果所參考的組件`pwzAssemblyIdentity`參數是強式命名，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="cfeae-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfeae-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="cfeae-108">Return Value</span></span>  
  
|<span data-ttu-id="cfeae-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfeae-109">HRESULT</span></span>|<span data-ttu-id="cfeae-110">描述</span><span class="sxs-lookup"><span data-stu-id="cfeae-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfeae-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfeae-111">S_OK</span></span>|<span data-ttu-id="cfeae-112">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="cfeae-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="cfeae-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cfeae-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cfeae-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cfeae-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cfeae-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cfeae-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cfeae-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="cfeae-116">The call timed out.</span></span>|  
|<span data-ttu-id="cfeae-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cfeae-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cfeae-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cfeae-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cfeae-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cfeae-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cfeae-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="cfeae-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cfeae-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfeae-121">E_FAIL</span></span>|<span data-ttu-id="cfeae-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfeae-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cfeae-123">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="cfeae-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cfeae-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cfeae-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cfeae-125">需求</span><span class="sxs-lookup"><span data-stu-id="cfeae-125">Requirements</span></span>  
 <span data-ttu-id="cfeae-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfeae-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfeae-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfeae-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfeae-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cfeae-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfeae-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfeae-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfeae-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfeae-130">See also</span></span>
- [<span data-ttu-id="cfeae-131">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="cfeae-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
