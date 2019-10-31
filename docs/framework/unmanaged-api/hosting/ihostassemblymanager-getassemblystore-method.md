---
title: IHostAssemblyManager::GetAssemblyStore 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 91c9a92d83312efcfd90a15aa0a60cccb6b44d7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134729"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="4696d-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="4696d-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="4696d-103">取得[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="4696d-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4696d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4696d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4696d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4696d-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="4696d-106">脫銷`IHostAssemblyStore` 實例的函式指標，如果主機未執行 `IHostAssemblyStore`，則為 null。</span><span class="sxs-lookup"><span data-stu-id="4696d-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4696d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4696d-107">Return Value</span></span>  
  
|<span data-ttu-id="4696d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4696d-108">HRESULT</span></span>|<span data-ttu-id="4696d-109">描述</span><span class="sxs-lookup"><span data-stu-id="4696d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4696d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4696d-110">S_OK</span></span>|<span data-ttu-id="4696d-111">已成功傳回 `GetAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="4696d-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="4696d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4696d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4696d-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4696d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4696d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4696d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4696d-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="4696d-115">The call timed out.</span></span>|  
|<span data-ttu-id="4696d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4696d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4696d-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4696d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4696d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4696d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4696d-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="4696d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4696d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4696d-120">E_FAIL</span></span>|<span data-ttu-id="4696d-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4696d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4696d-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="4696d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4696d-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4696d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4696d-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="4696d-124">E_NOINTERFACE</span></span>|<span data-ttu-id="4696d-125">主機未提供 `IHostAssemblyStore`的執行。</span><span class="sxs-lookup"><span data-stu-id="4696d-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4696d-126">備註</span><span class="sxs-lookup"><span data-stu-id="4696d-126">Remarks</span></span>  
 <span data-ttu-id="4696d-127">`IHostAssemblyStore` 提供的方法可讓主機與 CLR 分開系結至元件和模組。</span><span class="sxs-lookup"><span data-stu-id="4696d-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="4696d-128">主機通常會提供元件存放區，以允許從檔案系統以外的格式載入元件。</span><span class="sxs-lookup"><span data-stu-id="4696d-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4696d-129">如果主機未執行 `IHostAssemblyStore`，`GetAssemblyStore` 應該會傳回 E_NOINTERFACE 的 HRESULT 值，而且應該將 `ppAssemblyStore` 設定為 null。</span><span class="sxs-lookup"><span data-stu-id="4696d-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4696d-130">需求</span><span class="sxs-lookup"><span data-stu-id="4696d-130">Requirements</span></span>  
 <span data-ttu-id="4696d-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4696d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4696d-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4696d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4696d-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4696d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4696d-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4696d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4696d-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="4696d-135">See also</span></span>

- [<span data-ttu-id="4696d-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="4696d-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="4696d-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="4696d-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
