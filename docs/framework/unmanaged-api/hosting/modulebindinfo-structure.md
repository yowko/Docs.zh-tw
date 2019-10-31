---
title: ModuleBindInfo 結構
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133753"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="350de-102">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="350de-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="350de-103">提供參考模組和包含它之元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="350de-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350de-104">語法</span><span class="sxs-lookup"><span data-stu-id="350de-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="350de-105">Members</span><span class="sxs-lookup"><span data-stu-id="350de-105">Members</span></span>  
  
|<span data-ttu-id="350de-106">成員</span><span class="sxs-lookup"><span data-stu-id="350de-106">Member</span></span>|<span data-ttu-id="350de-107">描述</span><span class="sxs-lookup"><span data-stu-id="350de-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="350de-108">呼叫[IHostAssemblyStore：:P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)方法時所傳回之 `IStream` 的唯一識別碼，所參考的模組會從中載入。</span><span class="sxs-lookup"><span data-stu-id="350de-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="350de-109">包含參考模組之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="350de-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="350de-110">參考模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="350de-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="350de-111">備註</span><span class="sxs-lookup"><span data-stu-id="350de-111">Remarks</span></span>  
 <span data-ttu-id="350de-112">`ModuleBindInfo` 會當做參數傳遞給 `IHostAssemblyStore::ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="350de-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="350de-113">主機會將唯一識別碼提供給 common language runtime （CLR） `dwAppDomainId`。</span><span class="sxs-lookup"><span data-stu-id="350de-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="350de-114">呼叫[IHostAssemblyStore：:P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法之後，執行時間會使用識別碼來判斷是否已對應 `IStream` 的內容。</span><span class="sxs-lookup"><span data-stu-id="350de-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="350de-115">若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="350de-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="350de-116">執行時間也會使用這個識別碼做為從呼叫 `IHostAssemblyStore::ProvideAssembly` 方法所傳回之資料流程的查閱索引鍵。</span><span class="sxs-lookup"><span data-stu-id="350de-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="350de-117">因此，識別碼在模組要求和元件要求中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="350de-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="350de-118">需求</span><span class="sxs-lookup"><span data-stu-id="350de-118">Requirements</span></span>  
 <span data-ttu-id="350de-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="350de-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="350de-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="350de-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="350de-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="350de-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="350de-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="350de-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350de-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="350de-123">See also</span></span>

- [<span data-ttu-id="350de-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="350de-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="350de-125">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="350de-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="350de-126">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="350de-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="350de-127">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="350de-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="350de-128">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="350de-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
