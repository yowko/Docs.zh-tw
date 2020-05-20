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
ms.openlocfilehash: d388f366671f50c3dcb3bd9d387300dd1bbb168f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615900"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="eacf7-102">ICLRAssemblyIdentityManager::IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="eacf7-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="eacf7-103">取得值，指出指定的元件是否為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="eacf7-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eacf7-104">語法</span><span class="sxs-lookup"><span data-stu-id="eacf7-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eacf7-105">參數</span><span class="sxs-lookup"><span data-stu-id="eacf7-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="eacf7-106">在要評估之元件的不透明標準元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="eacf7-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="eacf7-107">[out] `true` ，如果參數所參考的元件 `pwzAssemblyIdentity` 是強式名稱，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="eacf7-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eacf7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eacf7-108">Return Value</span></span>  
  
|<span data-ttu-id="eacf7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eacf7-109">HRESULT</span></span>|<span data-ttu-id="eacf7-110">說明</span><span class="sxs-lookup"><span data-stu-id="eacf7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eacf7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eacf7-111">S_OK</span></span>|<span data-ttu-id="eacf7-112">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="eacf7-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="eacf7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eacf7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eacf7-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eacf7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eacf7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eacf7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eacf7-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eacf7-116">The call timed out.</span></span>|  
|<span data-ttu-id="eacf7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eacf7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eacf7-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eacf7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eacf7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eacf7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eacf7-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eacf7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eacf7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eacf7-121">E_FAIL</span></span>|<span data-ttu-id="eacf7-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eacf7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eacf7-123">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="eacf7-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eacf7-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eacf7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eacf7-125">需求</span><span class="sxs-lookup"><span data-stu-id="eacf7-125">Requirements</span></span>  
 <span data-ttu-id="eacf7-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eacf7-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eacf7-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="eacf7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eacf7-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eacf7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eacf7-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eacf7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eacf7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eacf7-130">See also</span></span>

- [<span data-ttu-id="eacf7-131">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="eacf7-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
