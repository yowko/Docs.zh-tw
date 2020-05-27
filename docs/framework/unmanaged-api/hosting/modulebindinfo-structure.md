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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006749"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="4bc4a-102">ModuleBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="4bc4a-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="4bc4a-103">提供參考模組和包含它之元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bc4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bc4a-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="4bc4a-105">成員</span><span class="sxs-lookup"><span data-stu-id="4bc4a-105">Members</span></span>  
  
|<span data-ttu-id="4bc4a-106">成員</span><span class="sxs-lookup"><span data-stu-id="4bc4a-106">Member</span></span>|<span data-ttu-id="4bc4a-107">描述</span><span class="sxs-lookup"><span data-stu-id="4bc4a-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="4bc4a-108">`IStream`呼叫[IHostAssemblyStore：:P rovidemodule](ihostassemblystore-providemodule-method.md)方法時所傳回的唯一識別碼，參考的模組會從中載入。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="4bc4a-109">包含參考模組之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="4bc4a-110">參考模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bc4a-111">備註</span><span class="sxs-lookup"><span data-stu-id="4bc4a-111">Remarks</span></span>  
 <span data-ttu-id="4bc4a-112">`ModuleBindInfo`會當做參數傳遞至 `IHostAssemblyStore::ProvideModule` 。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="4bc4a-113">主機會提供唯一識別碼 `dwAppDomainId` 給 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="4bc4a-114">呼叫[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md)方法之後，執行時間會使用識別碼來判斷的內容是否 `IStream` 已對應。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="4bc4a-115">若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="4bc4a-116">執行時間也會使用這個識別碼做為從呼叫方法所傳回之資料流程的查閱索引鍵 `IHostAssemblyStore::ProvideAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="4bc4a-117">因此，識別碼在模組要求和元件要求中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bc4a-118">需求</span><span class="sxs-lookup"><span data-stu-id="4bc4a-118">Requirements</span></span>  
 <span data-ttu-id="4bc4a-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bc4a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bc4a-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="4bc4a-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4bc4a-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4bc4a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bc4a-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bc4a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc4a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bc4a-123">See also</span></span>

- [<span data-ttu-id="4bc4a-124">裝載結構</span><span class="sxs-lookup"><span data-stu-id="4bc4a-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4bc4a-125">AssemblyBindInfo 結構</span><span class="sxs-lookup"><span data-stu-id="4bc4a-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="4bc4a-126">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="4bc4a-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4bc4a-127">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="4bc4a-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4bc4a-128">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="4bc4a-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
