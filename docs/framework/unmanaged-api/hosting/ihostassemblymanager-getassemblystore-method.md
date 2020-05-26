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
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805077"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="e5efd-102">IHostAssemblyManager::GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="e5efd-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="e5efd-103">取得[IHostAssemblyStore](ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="e5efd-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5efd-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5efd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5efd-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5efd-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="e5efd-106">脫銷實例的函式指標 `IHostAssemblyStore` ，如果主機未執行，則為 null `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="e5efd-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5efd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5efd-107">Return Value</span></span>  
  
|<span data-ttu-id="e5efd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5efd-108">HRESULT</span></span>|<span data-ttu-id="e5efd-109">描述</span><span class="sxs-lookup"><span data-stu-id="e5efd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5efd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5efd-110">S_OK</span></span>|<span data-ttu-id="e5efd-111">`GetAssemblyStore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e5efd-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="e5efd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5efd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5efd-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e5efd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5efd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5efd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5efd-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e5efd-115">The call timed out.</span></span>|  
|<span data-ttu-id="e5efd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5efd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5efd-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e5efd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5efd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5efd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5efd-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e5efd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5efd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5efd-120">E_FAIL</span></span>|<span data-ttu-id="e5efd-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e5efd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5efd-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e5efd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5efd-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e5efd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e5efd-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e5efd-124">E_NOINTERFACE</span></span>|<span data-ttu-id="e5efd-125">主機未提供的執行 `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="e5efd-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5efd-126">備註</span><span class="sxs-lookup"><span data-stu-id="e5efd-126">Remarks</span></span>  
 <span data-ttu-id="e5efd-127">`IHostAssemblyStore`提供的方法可讓主機與 CLR 獨立系結至元件和模組。</span><span class="sxs-lookup"><span data-stu-id="e5efd-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="e5efd-128">主機通常會提供元件存放區，以允許從檔案系統以外的格式載入元件。</span><span class="sxs-lookup"><span data-stu-id="e5efd-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5efd-129">如果主機未執行 `IHostAssemblyStore` ， `GetAssemblyStore` 應該會傳回 E_NOINTERFACE 的 HRESULT 值，而且應該將設定 `ppAssemblyStore` 為 null。</span><span class="sxs-lookup"><span data-stu-id="e5efd-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5efd-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="e5efd-130">Requirements</span></span>  
 <span data-ttu-id="e5efd-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5efd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5efd-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e5efd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5efd-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e5efd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5efd-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5efd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5efd-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5efd-135">See also</span></span>

- [<span data-ttu-id="e5efd-136">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="e5efd-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="e5efd-137">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="e5efd-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
