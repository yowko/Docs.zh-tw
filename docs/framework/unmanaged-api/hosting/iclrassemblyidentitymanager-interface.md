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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126617"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="31bb7-102">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="31bb7-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="31bb7-103">提供的方法可支援主機和元件的 common language runtime （CLR）之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="31bb7-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31bb7-104">方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-104">Methods</span></span>  
  
|<span data-ttu-id="31bb7-105">方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-105">Method</span></span>|<span data-ttu-id="31bb7-106">描述</span><span class="sxs-lookup"><span data-stu-id="31bb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31bb7-107">GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="31bb7-108">取得位於指定檔案路徑之元件的元件識別系結資料。</span><span class="sxs-lookup"><span data-stu-id="31bb7-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="31bb7-109">GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="31bb7-110">取得指定資料流程中元件的標準元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="31bb7-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="31bb7-111">GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="31bb7-112">從提供的部分元件識別清單中取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="31bb7-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="31bb7-113">GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="31bb7-114">取得具有指定身分識別之元件所參考之元件識別碼的[ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="31bb7-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="31bb7-115">GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="31bb7-116">取得[ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)實例，其中包含元件在指定檔案路徑中參考的元件清單。</span><span class="sxs-lookup"><span data-stu-id="31bb7-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="31bb7-117">GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="31bb7-118">取得 `ICLRReferenceAssemblyEnum` 物件的指標，其中包含指定的資料流程中元件所參考之元件的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="31bb7-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="31bb7-119">IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="31bb7-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="31bb7-120">取得值，指出指定的元件是否為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="31bb7-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31bb7-121">備註</span><span class="sxs-lookup"><span data-stu-id="31bb7-121">Remarks</span></span>  
 <span data-ttu-id="31bb7-122">使用 `ICLRAssemblyIdentityManager` 取得 `ICLRAssemblyReferenceList` 的實例並列舉元件身分識別。</span><span class="sxs-lookup"><span data-stu-id="31bb7-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31bb7-123">需求</span><span class="sxs-lookup"><span data-stu-id="31bb7-123">Requirements</span></span>  
 <span data-ttu-id="31bb7-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31bb7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31bb7-125">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="31bb7-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31bb7-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31bb7-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31bb7-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31bb7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31bb7-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="31bb7-128">See also</span></span>

- [<span data-ttu-id="31bb7-129">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="31bb7-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="31bb7-130">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="31bb7-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="31bb7-131">裝載介面</span><span class="sxs-lookup"><span data-stu-id="31bb7-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
