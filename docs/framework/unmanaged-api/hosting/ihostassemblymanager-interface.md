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
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805045"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="f7676-102">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="f7676-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="f7676-103">提供的方法可讓主機指定通用語言執行時間（CLR）或主機應載入的元件集。</span><span class="sxs-lookup"><span data-stu-id="f7676-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7676-104">方法</span><span class="sxs-lookup"><span data-stu-id="f7676-104">Methods</span></span>  
  
|<span data-ttu-id="f7676-105">方法</span><span class="sxs-lookup"><span data-stu-id="f7676-105">Method</span></span>|<span data-ttu-id="f7676-106">描述</span><span class="sxs-lookup"><span data-stu-id="f7676-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7676-107">GetAssemblyStore 方法</span><span class="sxs-lookup"><span data-stu-id="f7676-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="f7676-108">取得[IHostAssemblyStore](ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="f7676-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="f7676-109">GetNonHostStoreAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="f7676-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="f7676-110">取得[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)的介面指標，表示主機預期 CLR 載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="f7676-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7676-111">備註</span><span class="sxs-lookup"><span data-stu-id="f7676-111">Remarks</span></span>  
 <span data-ttu-id="f7676-112">不需要主機來執行 `IHostAssemblyManager` 或 `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="f7676-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="f7676-113">如果主機確實執行 `IHostAssemblyManager` ，它也必須執行 `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="f7676-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="f7676-114">執行時間會 `IHostAssemblyManager` 在初始化時呼叫[IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md) ，並使用 `IID` IID_IHostAssemblyManager 的來查詢。</span><span class="sxs-lookup"><span data-stu-id="f7676-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7676-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="f7676-115">Requirements</span></span>  
 <span data-ttu-id="f7676-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7676-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7676-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f7676-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7676-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7676-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7676-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7676-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7676-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7676-120">See also</span></span>

- [<span data-ttu-id="f7676-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="f7676-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f7676-122">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="f7676-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="f7676-123">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="f7676-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="f7676-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f7676-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
