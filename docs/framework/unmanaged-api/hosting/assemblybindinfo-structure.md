---
title: AssemblyBindInfo 結構
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0247f356bfc9f354edc420ea5460da02b17ab116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561136"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="dbc4f-102">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="dbc4f-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="dbc4f-103">提供參考的組件的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbc4f-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="dbc4f-105">成員</span><span class="sxs-lookup"><span data-stu-id="dbc4f-105">Members</span></span>  
  
|<span data-ttu-id="dbc4f-106">成員</span><span class="sxs-lookup"><span data-stu-id="dbc4f-106">Member</span></span>|<span data-ttu-id="dbc4f-107">描述</span><span class="sxs-lookup"><span data-stu-id="dbc4f-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="dbc4f-108">唯一識別碼`IStream`呼叫所傳回的[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)，從參考的組件即載入。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="dbc4f-109">參考的組件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="dbc4f-110">參考的組件之後的任何繫結的原則值的應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="dbc4f-111">其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出哪一個版本控制，如果有的話，應該套用原則的參考組件。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc4f-112">備註</span><span class="sxs-lookup"><span data-stu-id="dbc4f-112">Remarks</span></span>  
 <span data-ttu-id="dbc4f-113">主應用程式提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="dbc4f-114">在呼叫之後`IHostAssemblyStore::ProvideAssembly`傳回時，執行階段會使用識別碼來判斷是否內容`IStream`已經對應。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="dbc4f-115">如果是的話，則執行階段會載入現有的複本，而不是重新對應之資料流。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="dbc4f-116">執行階段也會使用此識別碼做為查閱索引鍵從傳回的資料流呼叫[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="dbc4f-117">因此，識別碼必須是唯一的模組要求，並針對組件要求。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc4f-118">需求</span><span class="sxs-lookup"><span data-stu-id="dbc4f-118">Requirements</span></span>  
 <span data-ttu-id="dbc4f-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc4f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc4f-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="dbc4f-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="dbc4f-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dbc4f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbc4f-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc4f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc4f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc4f-123">See also</span></span>
- [<span data-ttu-id="dbc4f-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="dbc4f-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="dbc4f-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbc4f-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dbc4f-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="dbc4f-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dbc4f-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbc4f-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="dbc4f-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="dbc4f-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="dbc4f-129">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="dbc4f-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
