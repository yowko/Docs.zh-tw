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
ms.openlocfilehash: dbaba00e029729fff5ad478a50134ff1e1858c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443446"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="601aa-102">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="601aa-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="601aa-103">提供參考的模組和包含它的組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="601aa-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="601aa-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="601aa-105">成員</span><span class="sxs-lookup"><span data-stu-id="601aa-105">Members</span></span>  
  
|<span data-ttu-id="601aa-106">成員</span><span class="sxs-lookup"><span data-stu-id="601aa-106">Member</span></span>|<span data-ttu-id="601aa-107">描述</span><span class="sxs-lookup"><span data-stu-id="601aa-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="601aa-108">唯一識別碼`IStream`呼叫所傳回[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)從中參照的模組已載入的方法。</span><span class="sxs-lookup"><span data-stu-id="601aa-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="601aa-109">組件，其中包含參考之的模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="601aa-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="601aa-110">參照的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="601aa-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="601aa-111">備註</span><span class="sxs-lookup"><span data-stu-id="601aa-111">Remarks</span></span>  
 <span data-ttu-id="601aa-112">`ModuleBindInfo` 會當做參數傳遞`IHostAssemblyStore::ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="601aa-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="601aa-113">主機提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="601aa-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="601aa-114">若要在呼叫之後[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法傳回時，執行階段使用的識別項來決定是否的內容`IStream`已經對應。</span><span class="sxs-lookup"><span data-stu-id="601aa-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="601aa-115">如果是這樣，執行階段會載入現有的複本，而非重新對應資料流。</span><span class="sxs-lookup"><span data-stu-id="601aa-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="601aa-116">執行階段也使用此識別碼做為查閱索引鍵，會從呼叫傳回的資料流的`IHostAssemblyStore::ProvideAssembly`方法。</span><span class="sxs-lookup"><span data-stu-id="601aa-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="601aa-117">因此，識別碼必須是唯一的模組要求和與組件的要求。</span><span class="sxs-lookup"><span data-stu-id="601aa-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="601aa-118">需求</span><span class="sxs-lookup"><span data-stu-id="601aa-118">Requirements</span></span>  
 <span data-ttu-id="601aa-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="601aa-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="601aa-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="601aa-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="601aa-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="601aa-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="601aa-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="601aa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601aa-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="601aa-123">See Also</span></span>  
 [<span data-ttu-id="601aa-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="601aa-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="601aa-125">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="601aa-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="601aa-126">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="601aa-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="601aa-127">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="601aa-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="601aa-128">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="601aa-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
