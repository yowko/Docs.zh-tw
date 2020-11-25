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
ms.openlocfilehash: 505015877985492edab4b761b379f33f1e5c6660
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729976"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="694fd-102">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="694fd-102">ModuleBindInfo Structure</span></span>

<span data-ttu-id="694fd-103">提供參考的模組和包含它的元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="694fd-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="694fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="694fd-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="694fd-105">成員</span><span class="sxs-lookup"><span data-stu-id="694fd-105">Members</span></span>  
  
|<span data-ttu-id="694fd-106">member</span><span class="sxs-lookup"><span data-stu-id="694fd-106">Member</span></span>|<span data-ttu-id="694fd-107">描述</span><span class="sxs-lookup"><span data-stu-id="694fd-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="694fd-108">的唯一識別碼 `IStream` ，它是由呼叫 [IHostAssemblyStore：:P rovidemodule](ihostassemblystore-providemodule-method.md) 方法所傳回，該方法是要從中載入參考的模組。</span><span class="sxs-lookup"><span data-stu-id="694fd-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="694fd-109">包含參考模組之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="694fd-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="694fd-110">參考模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="694fd-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="694fd-111">備註</span><span class="sxs-lookup"><span data-stu-id="694fd-111">Remarks</span></span>  

 <span data-ttu-id="694fd-112">`ModuleBindInfo` 以參數形式傳遞至 `IHostAssemblyStore::ProvideModule` 。</span><span class="sxs-lookup"><span data-stu-id="694fd-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="694fd-113">主機會將唯一識別碼提供 `dwAppDomainId` 給 common language runtime (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="694fd-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="694fd-114">在呼叫 [IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md) 方法之後，執行時間會使用此識別碼來判斷的內容是否已 `IStream` 對應。</span><span class="sxs-lookup"><span data-stu-id="694fd-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="694fd-115">如果是，執行時間會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="694fd-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="694fd-116">執行時間也會使用這個識別碼做為呼叫方法所傳回之資料流程的查閱索引鍵 `IHostAssemblyStore::ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="694fd-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="694fd-117">因此，識別碼對於模組要求以及元件要求都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="694fd-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="694fd-118">需求</span><span class="sxs-lookup"><span data-stu-id="694fd-118">Requirements</span></span>  

 <span data-ttu-id="694fd-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="694fd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="694fd-120">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="694fd-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="694fd-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="694fd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="694fd-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="694fd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="694fd-123">See also</span></span>

- [<span data-ttu-id="694fd-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="694fd-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="694fd-125">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="694fd-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="694fd-126">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="694fd-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="694fd-127">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="694fd-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="694fd-128">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="694fd-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
