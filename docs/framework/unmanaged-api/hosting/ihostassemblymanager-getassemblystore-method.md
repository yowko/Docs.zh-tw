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
ms.openlocfilehash: 35e38949ce945d93216daffd3c0d91dad6c8739b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092769"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="8f3bd-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="8f3bd-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="8f3bd-103">取得的介面指標[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)表示主應用程式所載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f3bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f3bd-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f3bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f3bd-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="8f3bd-106">[out]函式指標`IHostAssemblyStore`執行個體，則為 null，如果主機未實作`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f3bd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f3bd-107">Return Value</span></span>  
  
|<span data-ttu-id="8f3bd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f3bd-108">HRESULT</span></span>|<span data-ttu-id="8f3bd-109">描述</span><span class="sxs-lookup"><span data-stu-id="8f3bd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f3bd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f3bd-110">S_OK</span></span>|`GetAssemblyStore` <span data-ttu-id="8f3bd-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-111">returned successfully.</span></span>|  
|<span data-ttu-id="8f3bd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f3bd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f3bd-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f3bd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f3bd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f3bd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-115">The call timed out.</span></span>|  
|<span data-ttu-id="8f3bd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f3bd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f3bd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f3bd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f3bd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f3bd-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f3bd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f3bd-120">E_FAIL</span></span>|<span data-ttu-id="8f3bd-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f3bd-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f3bd-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f3bd-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8f3bd-124">E_NOINTERFACE</span></span>|<span data-ttu-id="8f3bd-125">主機並未提供的實作`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f3bd-126">備註</span><span class="sxs-lookup"><span data-stu-id="8f3bd-126">Remarks</span></span>  
 `IHostAssemblyStore` <span data-ttu-id="8f3bd-127">提供方法，可讓主應用程式繫結至組件和模組與 CLR 無關。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-127">provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="8f3bd-128">主機通常會提供以允許從非檔案系統中載入的組件的組件存放區。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f3bd-129">如果主機未實作`IHostAssemblyStore`，`GetAssemblyStore`應該會傳回 E_NOINTERFACE，HRESULT 值和應該設定`ppAssemblyStore`為 null。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f3bd-130">需求</span><span class="sxs-lookup"><span data-stu-id="8f3bd-130">Requirements</span></span>  
 <span data-ttu-id="8f3bd-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3bd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f3bd-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f3bd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f3bd-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8f3bd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8f3bd-134">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8f3bd-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f3bd-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f3bd-135">See also</span></span>

- [<span data-ttu-id="8f3bd-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8f3bd-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="8f3bd-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="8f3bd-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
