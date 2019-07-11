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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e0e877402daf27c375aedddf8922e919a546ae5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781171"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="98a15-102">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="98a15-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="98a15-103">提供參考的模組和包含它的組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="98a15-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a15-104">語法</span><span class="sxs-lookup"><span data-stu-id="98a15-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="98a15-105">成員</span><span class="sxs-lookup"><span data-stu-id="98a15-105">Members</span></span>  
  
|<span data-ttu-id="98a15-106">成員</span><span class="sxs-lookup"><span data-stu-id="98a15-106">Member</span></span>|<span data-ttu-id="98a15-107">描述</span><span class="sxs-lookup"><span data-stu-id="98a15-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="98a15-108">唯一識別碼`IStream`所傳回的呼叫所[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)從其中參考的模組是要載入的方法。</span><span class="sxs-lookup"><span data-stu-id="98a15-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="98a15-109">包含參考的模組之組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="98a15-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="98a15-110">參考的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="98a15-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a15-111">備註</span><span class="sxs-lookup"><span data-stu-id="98a15-111">Remarks</span></span>  
 <span data-ttu-id="98a15-112">`ModuleBindInfo` 做為參數傳遞`IHostAssemblyStore::ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="98a15-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="98a15-113">主應用程式提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="98a15-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="98a15-114">在呼叫之後[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法傳回時，執行階段會使用識別碼來判斷是否內容`IStream`已經對應。</span><span class="sxs-lookup"><span data-stu-id="98a15-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="98a15-115">如果是的話，則執行階段會載入現有的複本，而不是重新對應之資料流。</span><span class="sxs-lookup"><span data-stu-id="98a15-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="98a15-116">執行階段也會使用此識別碼做為查閱索引鍵，從呼叫傳回的資料流`IHostAssemblyStore::ProvideAssembly`方法。</span><span class="sxs-lookup"><span data-stu-id="98a15-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="98a15-117">因此，識別碼必須是唯一的模組要求也與組件要求。</span><span class="sxs-lookup"><span data-stu-id="98a15-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a15-118">需求</span><span class="sxs-lookup"><span data-stu-id="98a15-118">Requirements</span></span>  
 <span data-ttu-id="98a15-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98a15-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a15-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="98a15-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="98a15-121">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="98a15-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98a15-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a15-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a15-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a15-123">See also</span></span>

- [<span data-ttu-id="98a15-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="98a15-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="98a15-125">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="98a15-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="98a15-126">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="98a15-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="98a15-127">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="98a15-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="98a15-128">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="98a15-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
