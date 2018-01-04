---
title: "IHostAssemblyManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 351824c1b915183a8e157f5bb2e01a414027a178
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="e76af-102">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="e76af-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="e76af-103">提供方法，讓主應用程式指定的 common language runtime (CLR) 或主應用程式應該載入的組件集合。</span><span class="sxs-lookup"><span data-stu-id="e76af-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e76af-104">方法</span><span class="sxs-lookup"><span data-stu-id="e76af-104">Methods</span></span>  
  
|<span data-ttu-id="e76af-105">方法</span><span class="sxs-lookup"><span data-stu-id="e76af-105">Method</span></span>|<span data-ttu-id="e76af-106">描述</span><span class="sxs-lookup"><span data-stu-id="e76af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e76af-107">GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="e76af-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="e76af-108">取得的介面指標[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)代表主應用程式載入的組件的清單。</span><span class="sxs-lookup"><span data-stu-id="e76af-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="e76af-109">GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="e76af-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="e76af-110">取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)表示主機必須要有 CLR 載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="e76af-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e76af-111">備註</span><span class="sxs-lookup"><span data-stu-id="e76af-111">Remarks</span></span>  
 <span data-ttu-id="e76af-112">主機不需要實作`IHostAssemblyManager`或`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="e76af-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="e76af-113">如果主應用程式確實有實作`IHostAssemblyManager`，也必須實作`IHostAssemblyStore`。</span><span class="sxs-lookup"><span data-stu-id="e76af-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="e76af-114">執行階段會查詢以取得`IHostAssemblyManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)時使用的初始化`IID`IID_IHostAssemblyManager。</span><span class="sxs-lookup"><span data-stu-id="e76af-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e76af-115">需求</span><span class="sxs-lookup"><span data-stu-id="e76af-115">Requirements</span></span>  
 <span data-ttu-id="e76af-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e76af-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e76af-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e76af-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e76af-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e76af-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e76af-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e76af-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76af-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="e76af-120">See Also</span></span>  
 [<span data-ttu-id="e76af-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="e76af-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="e76af-122">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="e76af-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="e76af-123">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="e76af-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="e76af-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e76af-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
