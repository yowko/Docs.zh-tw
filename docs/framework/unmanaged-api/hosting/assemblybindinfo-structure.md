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
ms.openlocfilehash: d2ba7d8e66472f771a932a2dfb05bb9e1ee96290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685873"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="0ec97-102">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="0ec97-102">AssemblyBindInfo Structure</span></span>

<span data-ttu-id="0ec97-103">提供參考元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0ec97-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec97-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ec97-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="0ec97-105">成員</span><span class="sxs-lookup"><span data-stu-id="0ec97-105">Members</span></span>  
  
|<span data-ttu-id="0ec97-106">member</span><span class="sxs-lookup"><span data-stu-id="0ec97-106">Member</span></span>|<span data-ttu-id="0ec97-107">描述</span><span class="sxs-lookup"><span data-stu-id="0ec97-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="0ec97-108">`IStream`由呼叫[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md)所傳回之的唯一識別碼，會從此處載入參考的元件。</span><span class="sxs-lookup"><span data-stu-id="0ec97-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="0ec97-109">參考元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="0ec97-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="0ec97-110">在應用任何系結原則值之後，所參考元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0ec97-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="0ec97-111">其中一個 [EPolicyAction](epolicyaction-enumeration.md) 值，指出應該套用至參考元件的版本控制原則（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="0ec97-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ec97-112">備註</span><span class="sxs-lookup"><span data-stu-id="0ec97-112">Remarks</span></span>  

 <span data-ttu-id="0ec97-113">主機會將唯一識別碼提供 `dwAppDomainId` 給 common language runtime (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="0ec97-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="0ec97-114">在呼叫傳回之後 `IHostAssemblyStore::ProvideAssembly` ，執行時間會使用識別碼來判斷的內容是否 `IStream` 已對應。</span><span class="sxs-lookup"><span data-stu-id="0ec97-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="0ec97-115">如果是，執行時間會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="0ec97-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="0ec97-116">執行時間也會使用此識別碼作為從呼叫 [IHostAssemblyStore：:P rovidemodule](ihostassemblystore-providemodule-method.md)所傳回之資料流程的查閱索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0ec97-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="0ec97-117">因此，識別碼對於模組要求和元件要求而言必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0ec97-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec97-118">需求</span><span class="sxs-lookup"><span data-stu-id="0ec97-118">Requirements</span></span>  

 <span data-ttu-id="0ec97-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ec97-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec97-120">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0ec97-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0ec97-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0ec97-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ec97-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec97-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec97-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec97-123">See also</span></span>

- [<span data-ttu-id="0ec97-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="0ec97-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="0ec97-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ec97-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0ec97-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="0ec97-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0ec97-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ec97-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="0ec97-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="0ec97-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="0ec97-129">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="0ec97-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
