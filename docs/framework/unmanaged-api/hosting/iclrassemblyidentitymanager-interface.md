---
title: "ICLRAssemblyIdentityManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="761ce-102">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="761ce-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="761ce-103">提供方法來支援主應用程式與 common language runtime (CLR) 關於組件之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="761ce-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="761ce-104">方法</span><span class="sxs-lookup"><span data-stu-id="761ce-104">Methods</span></span>  
  
|<span data-ttu-id="761ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="761ce-105">Method</span></span>|<span data-ttu-id="761ce-106">描述</span><span class="sxs-lookup"><span data-stu-id="761ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="761ce-107">GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="761ce-108">取得位於指定的檔案路徑的組件的繫結資料的組件識別。</span><span class="sxs-lookup"><span data-stu-id="761ce-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="761ce-109">GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="761ce-110">取得指定的資料流中的組件的標準的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="761ce-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="761ce-111">GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="761ce-112">取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從提供的清單執行個體的部分組件識別。</span><span class="sxs-lookup"><span data-stu-id="761ce-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="761ce-113">GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="761ce-114">取得[ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)具有指定識別組件所參考的組件識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="761ce-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="761ce-115">GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="761ce-116">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)包含在指定的檔案路徑的組件所參考的組件清單的執行個體。</span><span class="sxs-lookup"><span data-stu-id="761ce-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="761ce-117">GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="761ce-118">取得指標`ICLRReferenceAssemblyEnum`物件，其中包含指定的資料流中的組件所參考之組件的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="761ce-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="761ce-119">IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="761ce-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="761ce-120">取得值，指出是否指定的組件強式名稱。</span><span class="sxs-lookup"><span data-stu-id="761ce-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="761ce-121">備註</span><span class="sxs-lookup"><span data-stu-id="761ce-121">Remarks</span></span>  
 <span data-ttu-id="761ce-122">使用`ICLRAssemblyIdentityManager`取得的執行個體`ICLRAssemblyReferenceList`和要列舉的組件識別。</span><span class="sxs-lookup"><span data-stu-id="761ce-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="761ce-123">需求</span><span class="sxs-lookup"><span data-stu-id="761ce-123">Requirements</span></span>  
 <span data-ttu-id="761ce-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="761ce-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="761ce-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="761ce-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="761ce-126">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="761ce-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="761ce-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="761ce-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761ce-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="761ce-128">See Also</span></span>  
 [<span data-ttu-id="761ce-129">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="761ce-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="761ce-130">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="761ce-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="761ce-131">裝載介面</span><span class="sxs-lookup"><span data-stu-id="761ce-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
