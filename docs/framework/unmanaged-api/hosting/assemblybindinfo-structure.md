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
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192105"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="764b9-102">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="764b9-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="764b9-103">提供有關所參考元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="764b9-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="764b9-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="764b9-105">Members</span><span class="sxs-lookup"><span data-stu-id="764b9-105">Members</span></span>  
  
|<span data-ttu-id="764b9-106">成員</span><span class="sxs-lookup"><span data-stu-id="764b9-106">Member</span></span>|<span data-ttu-id="764b9-107">描述</span><span class="sxs-lookup"><span data-stu-id="764b9-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="764b9-108">呼叫[IHostAssemblyStore：:P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)所傳回之 `IStream` 的唯一識別碼，所參考的元件會從中載入。</span><span class="sxs-lookup"><span data-stu-id="764b9-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="764b9-109">參考元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="764b9-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="764b9-110">應用程式的任何系結原則值之後，所參考元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="764b9-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="764b9-111">其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出哪些版本設定原則（如果有的話）應套用至參考的元件。</span><span class="sxs-lookup"><span data-stu-id="764b9-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="764b9-112">備註</span><span class="sxs-lookup"><span data-stu-id="764b9-112">Remarks</span></span>  
 <span data-ttu-id="764b9-113">主機會將唯一識別碼提供給 common language runtime （CLR） `dwAppDomainId`。</span><span class="sxs-lookup"><span data-stu-id="764b9-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="764b9-114">呼叫 `IHostAssemblyStore::ProvideAssembly` 傳回之後，執行時間會使用識別碼來判斷是否已對應 `IStream` 的內容。</span><span class="sxs-lookup"><span data-stu-id="764b9-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="764b9-115">若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="764b9-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="764b9-116">執行時間也會使用此識別碼作為從呼叫 IHostAssemblyStore 所傳回之資料流程的查閱索引鍵[：:P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。</span><span class="sxs-lookup"><span data-stu-id="764b9-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="764b9-117">因此，對於模組要求和元件要求而言，識別碼必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="764b9-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764b9-118">需求</span><span class="sxs-lookup"><span data-stu-id="764b9-118">Requirements</span></span>  
 <span data-ttu-id="764b9-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="764b9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764b9-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="764b9-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="764b9-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="764b9-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="764b9-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764b9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764b9-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="764b9-123">See also</span></span>

- [<span data-ttu-id="764b9-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="764b9-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="764b9-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="764b9-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="764b9-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="764b9-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="764b9-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="764b9-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="764b9-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="764b9-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="764b9-129">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="764b9-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
