---
title: "AssemblyBindInfo 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="baa42-102">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="baa42-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="baa42-103">提供參考組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="baa42-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa42-104">語法</span><span class="sxs-lookup"><span data-stu-id="baa42-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="baa42-105">成員</span><span class="sxs-lookup"><span data-stu-id="baa42-105">Members</span></span>  
  
|<span data-ttu-id="baa42-106">成員</span><span class="sxs-lookup"><span data-stu-id="baa42-106">Member</span></span>|<span data-ttu-id="baa42-107">說明</span><span class="sxs-lookup"><span data-stu-id="baa42-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="baa42-108">唯一識別碼`IStream`呼叫所傳回的[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)，從參考組件即載入。</span><span class="sxs-lookup"><span data-stu-id="baa42-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="baa42-109">參考的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="baa42-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="baa42-110">參考的組件之後的任何繫結的原則值的應用程式識別項。</span><span class="sxs-lookup"><span data-stu-id="baa42-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="baa42-111">其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出哪一個版本控制原則，如果有的話，應該套用到參考的組件。</span><span class="sxs-lookup"><span data-stu-id="baa42-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baa42-112">備註</span><span class="sxs-lookup"><span data-stu-id="baa42-112">Remarks</span></span>  
 <span data-ttu-id="baa42-113">主機提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="baa42-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="baa42-114">若要在呼叫之後`IHostAssemblyStore::ProvideAssembly`傳回時，執行階段使用的識別項來決定是否的內容`IStream`已經對應。</span><span class="sxs-lookup"><span data-stu-id="baa42-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="baa42-115">如果是這樣，執行階段會載入現有的複本，而非重新對應資料流。</span><span class="sxs-lookup"><span data-stu-id="baa42-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="baa42-116">執行階段也會使用這個識別碼做為查閱索引鍵以從傳回的資料流呼叫[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。</span><span class="sxs-lookup"><span data-stu-id="baa42-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="baa42-117">因此，識別碼必須是唯一的要求模組和組件要求。</span><span class="sxs-lookup"><span data-stu-id="baa42-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa42-118">需求</span><span class="sxs-lookup"><span data-stu-id="baa42-118">Requirements</span></span>  
 <span data-ttu-id="baa42-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baa42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa42-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="baa42-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="baa42-121">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="baa42-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baa42-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa42-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa42-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baa42-123">See Also</span></span>  
 [<span data-ttu-id="baa42-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="baa42-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="baa42-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="baa42-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="baa42-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="baa42-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="baa42-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="baa42-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="baa42-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="baa42-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="baa42-129">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="baa42-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
