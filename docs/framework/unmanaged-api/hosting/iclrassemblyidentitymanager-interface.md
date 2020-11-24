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
ms.openlocfilehash: 41d049c931091d2cc0b41bd1e9d74b3c15d7878d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679256"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="dbeb7-102">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbeb7-102">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="dbeb7-103">提供方法，可支援主機和 common language runtime 之間的通訊， (CLR) 有關元件的資訊。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbeb7-104">方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-104">Methods</span></span>  
  
|<span data-ttu-id="dbeb7-105">方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-105">Method</span></span>|<span data-ttu-id="dbeb7-106">描述</span><span class="sxs-lookup"><span data-stu-id="dbeb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbeb7-107">GetBindingIdentityFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="dbeb7-108">取得位於指定檔案路徑之元件的元件識別系結資料。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="dbeb7-109">GetBindingIdentityFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="dbeb7-110">取得指定之資料流程中元件的標準元件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="dbeb7-111">GetCLRAssemblyReferenceList 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-111">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="dbeb7-112">從提供的部分元件身分識別清單取得 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="dbeb7-113">GetProbingAssembliesFromReference 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-113">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="dbeb7-114">取得元件的 [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列舉值，該元件是由具有指定身分識別的元件所參考。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="dbeb7-115">GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-115">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="dbeb7-116">取得 [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) 實例，其中包含元件在指定檔案路徑所參考的元件清單。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="dbeb7-117">GetReferencedAssembliesFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="dbeb7-118">取得 `ICLRReferenceAssemblyEnum` 物件的指標，該物件包含指定資料流程中元件所參考之元件的元件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="dbeb7-119">IsStronglyNamed 方法</span><span class="sxs-lookup"><span data-stu-id="dbeb7-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="dbeb7-120">取得值，這個值會指出指定的元件是否為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbeb7-121">備註</span><span class="sxs-lookup"><span data-stu-id="dbeb7-121">Remarks</span></span>  

 <span data-ttu-id="dbeb7-122">使用 `ICLRAssemblyIdentityManager` 取得的實例 `ICLRAssemblyReferenceList` 和，以列舉元件身分識別。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbeb7-123">需求</span><span class="sxs-lookup"><span data-stu-id="dbeb7-123">Requirements</span></span>  

 <span data-ttu-id="dbeb7-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbeb7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbeb7-125">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dbeb7-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbeb7-126">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="dbeb7-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbeb7-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbeb7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbeb7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbeb7-128">See also</span></span>

- [<span data-ttu-id="dbeb7-129">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="dbeb7-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dbeb7-130">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dbeb7-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="dbeb7-131">裝載介面</span><span class="sxs-lookup"><span data-stu-id="dbeb7-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
