---
title: IHostAssemblyManager 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: d9feeaf5f85d6f84a13e74a893b82c97fdaf023c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124514"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="7fc66-102">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="7fc66-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="7fc66-103">提供的方法可讓主機指定通用語言執行時間（CLR）或主機應載入的元件集。</span><span class="sxs-lookup"><span data-stu-id="7fc66-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fc66-104">方法</span><span class="sxs-lookup"><span data-stu-id="7fc66-104">Methods</span></span>  
  
|<span data-ttu-id="7fc66-105">方法</span><span class="sxs-lookup"><span data-stu-id="7fc66-105">Method</span></span>|<span data-ttu-id="7fc66-106">描述</span><span class="sxs-lookup"><span data-stu-id="7fc66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fc66-107">GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="7fc66-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="7fc66-108">取得[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="7fc66-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="7fc66-109">GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="7fc66-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="7fc66-110">取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)的介面指標，表示主機預期 CLR 載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="7fc66-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fc66-111">備註</span><span class="sxs-lookup"><span data-stu-id="7fc66-111">Remarks</span></span>  
 <span data-ttu-id="7fc66-112">不需要主機來執行 `IHostAssemblyManager` 或 `IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="7fc66-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="7fc66-113">如果主機確實執行 `IHostAssemblyManager`，它也必須執行 `IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="7fc66-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="7fc66-114">執行時間會在初始化時透過呼叫[IHostControl：： GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)來查詢 `IHostAssemblyManager`，其中包含 IID_IHostAssemblyManager 的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="7fc66-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc66-115">需求</span><span class="sxs-lookup"><span data-stu-id="7fc66-115">Requirements</span></span>  
 <span data-ttu-id="7fc66-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7fc66-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc66-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7fc66-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fc66-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7fc66-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fc66-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc66-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc66-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fc66-120">See also</span></span>

- [<span data-ttu-id="7fc66-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="7fc66-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7fc66-122">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="7fc66-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="7fc66-123">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="7fc66-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="7fc66-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7fc66-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
