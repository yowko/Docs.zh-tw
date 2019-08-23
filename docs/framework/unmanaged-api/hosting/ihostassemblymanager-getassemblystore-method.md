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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62965fa928522052b6885769e02c0211ca8d3fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937939"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="f1bbc-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="f1bbc-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="f1bbc-103">取得[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的介面指標, 表示主機所載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1bbc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1bbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1bbc-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="f1bbc-106">脫銷`IHostAssemblyStore`實例的函式指標, 如果主機未執行`IHostAssemblyStore`, 則為 null。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1bbc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1bbc-107">Return Value</span></span>  
  
|<span data-ttu-id="f1bbc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1bbc-108">HRESULT</span></span>|<span data-ttu-id="f1bbc-109">描述</span><span class="sxs-lookup"><span data-stu-id="f1bbc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1bbc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1bbc-110">S_OK</span></span>|<span data-ttu-id="f1bbc-111">`GetAssemblyStore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="f1bbc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1bbc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1bbc-113">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1bbc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1bbc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1bbc-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-115">The call timed out.</span></span>|  
|<span data-ttu-id="f1bbc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1bbc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1bbc-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1bbc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1bbc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1bbc-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1bbc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1bbc-120">E_FAIL</span></span>|<span data-ttu-id="f1bbc-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1bbc-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1bbc-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f1bbc-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="f1bbc-124">E_NOINTERFACE</span></span>|<span data-ttu-id="f1bbc-125">主機未提供的`IHostAssemblyStore`執行。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1bbc-126">備註</span><span class="sxs-lookup"><span data-stu-id="f1bbc-126">Remarks</span></span>  
 <span data-ttu-id="f1bbc-127">`IHostAssemblyStore`提供的方法可讓主機與 CLR 獨立系結至元件和模組。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="f1bbc-128">主機通常會提供元件存放區, 以允許從檔案系統以外的格式載入元件。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1bbc-129">如果主機未執行`IHostAssemblyStore`, `GetAssemblyStore`應該會傳回 E_NOINTERFACE 的 HRESULT 值, 而且應該將設定`ppAssemblyStore`為 null。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1bbc-130">需求</span><span class="sxs-lookup"><span data-stu-id="f1bbc-130">Requirements</span></span>  
 <span data-ttu-id="f1bbc-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bbc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bbc-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1bbc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1bbc-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f1bbc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1bbc-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bbc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bbc-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1bbc-135">See also</span></span>

- [<span data-ttu-id="f1bbc-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="f1bbc-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="f1bbc-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="f1bbc-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
