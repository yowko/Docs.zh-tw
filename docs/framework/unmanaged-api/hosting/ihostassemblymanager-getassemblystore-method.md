---
title: "IHostAssemblyManager::GetAssemblyStore 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d838ee8383a4e11f5d43c4a3751c4a90503906fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="17efd-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="17efd-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="17efd-103">取得的介面指標[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)代表主應用程式載入的組件的清單。</span><span class="sxs-lookup"><span data-stu-id="17efd-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17efd-104">語法</span><span class="sxs-lookup"><span data-stu-id="17efd-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17efd-105">參數</span><span class="sxs-lookup"><span data-stu-id="17efd-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="17efd-106">[out]函式指標至`IHostAssemblyStore`執行個體，則為 null，如果主機未實作`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="17efd-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17efd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="17efd-107">Return Value</span></span>  
  
|<span data-ttu-id="17efd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17efd-108">HRESULT</span></span>|<span data-ttu-id="17efd-109">描述</span><span class="sxs-lookup"><span data-stu-id="17efd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17efd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="17efd-110">S_OK</span></span>|<span data-ttu-id="17efd-111">`GetAssemblyStore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="17efd-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="17efd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17efd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17efd-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="17efd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17efd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17efd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17efd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="17efd-115">The call timed out.</span></span>|  
|<span data-ttu-id="17efd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17efd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17efd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="17efd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17efd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17efd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17efd-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="17efd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17efd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17efd-120">E_FAIL</span></span>|<span data-ttu-id="17efd-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="17efd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17efd-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="17efd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17efd-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="17efd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="17efd-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="17efd-124">E_NOINTERFACE</span></span>|<span data-ttu-id="17efd-125">主機並未提供的實作`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="17efd-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17efd-126">備註</span><span class="sxs-lookup"><span data-stu-id="17efd-126">Remarks</span></span>  
 <span data-ttu-id="17efd-127">`IHostAssemblyStore`提供方法，讓主應用程式繫結至組件和模組與 CLR 無關。</span><span class="sxs-lookup"><span data-stu-id="17efd-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="17efd-128">主機通常會提供以允許從檔案系統以外的格式中載入的組件的組件存放區。</span><span class="sxs-lookup"><span data-stu-id="17efd-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17efd-129">如果主機未實作`IHostAssemblyStore`，`GetAssemblyStore`應該會傳回 E_NOINTERFACE，HRESULT 值，來設定`ppAssemblyStore`為 null。</span><span class="sxs-lookup"><span data-stu-id="17efd-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17efd-130">需求</span><span class="sxs-lookup"><span data-stu-id="17efd-130">Requirements</span></span>  
 <span data-ttu-id="17efd-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17efd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17efd-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17efd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17efd-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="17efd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17efd-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17efd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17efd-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17efd-135">See Also</span></span>  
 [<span data-ttu-id="17efd-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="17efd-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="17efd-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="17efd-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
