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
ms.openlocfilehash: 936ea068f3cc5567a00af5f2bdd5f3d9cd52bc81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681180"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="12ef6-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="12ef6-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>

<span data-ttu-id="12ef6-103">取得 [IHostAssemblyStore](ihostassemblystore-interface.md) 的介面指標，該指標表示主機載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="12ef6-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ef6-104">語法</span><span class="sxs-lookup"><span data-stu-id="12ef6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12ef6-105">參數</span><span class="sxs-lookup"><span data-stu-id="12ef6-105">Parameters</span></span>  

 `ppAssemblyStore`  
 <span data-ttu-id="12ef6-106">擴展實例的函式指標 `IHostAssemblyStore` ，如果主機沒有執行，則為 null `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="12ef6-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12ef6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="12ef6-107">Return Value</span></span>  
  
|<span data-ttu-id="12ef6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12ef6-108">HRESULT</span></span>|<span data-ttu-id="12ef6-109">描述</span><span class="sxs-lookup"><span data-stu-id="12ef6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12ef6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="12ef6-110">S_OK</span></span>|<span data-ttu-id="12ef6-111">`GetAssemblyStore` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="12ef6-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="12ef6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12ef6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12ef6-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="12ef6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12ef6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12ef6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12ef6-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="12ef6-115">The call timed out.</span></span>|  
|<span data-ttu-id="12ef6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12ef6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12ef6-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="12ef6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12ef6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12ef6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12ef6-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="12ef6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12ef6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12ef6-120">E_FAIL</span></span>|<span data-ttu-id="12ef6-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="12ef6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12ef6-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="12ef6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12ef6-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="12ef6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="12ef6-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="12ef6-124">E_NOINTERFACE</span></span>|<span data-ttu-id="12ef6-125">主機未提供的實作為 `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="12ef6-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12ef6-126">備註</span><span class="sxs-lookup"><span data-stu-id="12ef6-126">Remarks</span></span>  

 <span data-ttu-id="12ef6-127">`IHostAssemblyStore` 提供可讓主機與 CLR 分開系結至元件和模組的方法。</span><span class="sxs-lookup"><span data-stu-id="12ef6-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="12ef6-128">主機通常會提供元件存放區，以允許從檔案系統以外的格式載入元件。</span><span class="sxs-lookup"><span data-stu-id="12ef6-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12ef6-129">如果主機未執行，則 `IHostAssemblyStore` `GetAssemblyStore` 應該傳回 E_NOINTERFACE 的 HRESULT 值，而且應該設 `ppAssemblyStore` 為 null。</span><span class="sxs-lookup"><span data-stu-id="12ef6-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ef6-130">需求</span><span class="sxs-lookup"><span data-stu-id="12ef6-130">Requirements</span></span>  

 <span data-ttu-id="12ef6-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12ef6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ef6-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="12ef6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12ef6-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="12ef6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12ef6-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ef6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ef6-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12ef6-135">See also</span></span>

- [<span data-ttu-id="12ef6-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="12ef6-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="12ef6-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="12ef6-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
