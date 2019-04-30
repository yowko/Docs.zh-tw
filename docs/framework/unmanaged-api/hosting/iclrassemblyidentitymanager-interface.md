---
title: ICLRAssemblyIdentityManager 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985032"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="9560e-102">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="9560e-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="9560e-103">提供方法來支援主應用程式和有關組件的 common language runtime (CLR) 之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="9560e-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9560e-104">方法</span><span class="sxs-lookup"><span data-stu-id="9560e-104">Methods</span></span>  
  
|<span data-ttu-id="9560e-105">方法</span><span class="sxs-lookup"><span data-stu-id="9560e-105">Method</span></span>|<span data-ttu-id="9560e-106">描述</span><span class="sxs-lookup"><span data-stu-id="9560e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9560e-107">GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="9560e-108">取得資料繫結在指定的檔案路徑組件的組件識別。</span><span class="sxs-lookup"><span data-stu-id="9560e-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="9560e-109">GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="9560e-110">取得指定的資料流中的組件的標準組件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="9560e-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="9560e-111">GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="9560e-112">取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)提供的清單中的部分組件身分識別執行個體。</span><span class="sxs-lookup"><span data-stu-id="9560e-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="9560e-113">GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="9560e-114">取得[ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)具有指定的身分識別的組件所參考的組件身分識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9560e-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="9560e-115">GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="9560e-116">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)包含一份在指定的檔案路徑組件所參考的組件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9560e-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="9560e-117">GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="9560e-118">取得指標`ICLRReferenceAssemblyEnum`物件，其中包含指定的資料流中的組件所參考的組件的組件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="9560e-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="9560e-119">IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="9560e-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="9560e-120">取得值，指出是否指定的組件強式名稱。</span><span class="sxs-lookup"><span data-stu-id="9560e-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9560e-121">備註</span><span class="sxs-lookup"><span data-stu-id="9560e-121">Remarks</span></span>  
 <span data-ttu-id="9560e-122">使用`ICLRAssemblyIdentityManager`若要取得的執行個體`ICLRAssemblyReferenceList`以及列舉組件識別。</span><span class="sxs-lookup"><span data-stu-id="9560e-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9560e-123">需求</span><span class="sxs-lookup"><span data-stu-id="9560e-123">Requirements</span></span>  
 <span data-ttu-id="9560e-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9560e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9560e-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9560e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9560e-126">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9560e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9560e-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9560e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9560e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9560e-128">See also</span></span>

- [<span data-ttu-id="9560e-129">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="9560e-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9560e-130">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9560e-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="9560e-131">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9560e-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
