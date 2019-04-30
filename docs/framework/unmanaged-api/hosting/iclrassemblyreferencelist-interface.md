---
title: ICLRAssemblyReferenceList 介面
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43c40e833e3a250239e9e90667196a2a74a96e0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969958"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="432cf-102">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="432cf-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="432cf-103">管理組件載入 common language runtime (CLR)，而不是由主應用程式的清單。</span><span class="sxs-lookup"><span data-stu-id="432cf-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="432cf-104">方法</span><span class="sxs-lookup"><span data-stu-id="432cf-104">Methods</span></span>  
  
|<span data-ttu-id="432cf-105">方法</span><span class="sxs-lookup"><span data-stu-id="432cf-105">Method</span></span>|<span data-ttu-id="432cf-106">描述</span><span class="sxs-lookup"><span data-stu-id="432cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="432cf-107">IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="432cf-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="432cf-108">取得值，指出是否提供的指標參考的組件清單中。</span><span class="sxs-lookup"><span data-stu-id="432cf-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="432cf-109">IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="432cf-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="432cf-110">取得值，指出提供的名稱是否符合清單中的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="432cf-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="432cf-111">備註</span><span class="sxs-lookup"><span data-stu-id="432cf-111">Remarks</span></span>  
 <span data-ttu-id="432cf-112">呼叫[iclrassemblyidentitymanager:: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)方法來取得的執行個體的指標`ICLRAssemblyReferenceList`。</span><span class="sxs-lookup"><span data-stu-id="432cf-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="432cf-113">需求</span><span class="sxs-lookup"><span data-stu-id="432cf-113">Requirements</span></span>  
 <span data-ttu-id="432cf-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="432cf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="432cf-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="432cf-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="432cf-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="432cf-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="432cf-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="432cf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432cf-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="432cf-118">See also</span></span>

- [<span data-ttu-id="432cf-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="432cf-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="432cf-120">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="432cf-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="432cf-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="432cf-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
