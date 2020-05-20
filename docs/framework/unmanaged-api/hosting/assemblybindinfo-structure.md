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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616914"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="02872-102">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="02872-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="02872-103">提供有關所參考元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="02872-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02872-104">語法</span><span class="sxs-lookup"><span data-stu-id="02872-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="02872-105">成員</span><span class="sxs-lookup"><span data-stu-id="02872-105">Members</span></span>  
  
|<span data-ttu-id="02872-106">成員</span><span class="sxs-lookup"><span data-stu-id="02872-106">Member</span></span>|<span data-ttu-id="02872-107">說明</span><span class="sxs-lookup"><span data-stu-id="02872-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="02872-108">`IStream`呼叫[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md)所傳回的唯一識別碼，參考的元件會從此處載入。</span><span class="sxs-lookup"><span data-stu-id="02872-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="02872-109">參考元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="02872-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="02872-110">應用程式的任何系結原則值之後，所參考元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="02872-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="02872-111">其中一個[EPolicyAction](epolicyaction-enumeration.md)值，指出哪些版本設定原則（如果有的話）應套用至參考的元件。</span><span class="sxs-lookup"><span data-stu-id="02872-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02872-112">備註</span><span class="sxs-lookup"><span data-stu-id="02872-112">Remarks</span></span>  
 <span data-ttu-id="02872-113">主機會提供唯一識別碼 `dwAppDomainId` 給 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="02872-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="02872-114">呼叫傳回之後 `IHostAssemblyStore::ProvideAssembly` ，執行時間會使用識別碼來判斷的內容是否 `IStream` 已對應。</span><span class="sxs-lookup"><span data-stu-id="02872-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="02872-115">若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="02872-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="02872-116">執行時間也會使用此識別碼作為從呼叫 IHostAssemblyStore 所傳回之資料流程的查閱索引鍵[：:P rovidemodule](ihostassemblystore-providemodule-method.md)。</span><span class="sxs-lookup"><span data-stu-id="02872-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="02872-117">因此，對於模組要求和元件要求而言，識別碼必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="02872-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02872-118">需求</span><span class="sxs-lookup"><span data-stu-id="02872-118">Requirements</span></span>  
 <span data-ttu-id="02872-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02872-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02872-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="02872-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="02872-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="02872-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02872-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02872-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02872-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02872-123">See also</span></span>

- [<span data-ttu-id="02872-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="02872-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="02872-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="02872-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="02872-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="02872-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="02872-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="02872-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="02872-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="02872-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="02872-129">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="02872-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
