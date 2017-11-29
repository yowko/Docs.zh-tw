---
title: "ICLRAssemblyReferenceList 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList
helpviewer_keywords: ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4249616ca46fe5ef09dce4a3e245794a103298c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="acc2c-102">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="acc2c-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="acc2c-103">管理由 common language runtime (CLR)，而不是由主應用程式載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="acc2c-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acc2c-104">方法</span><span class="sxs-lookup"><span data-stu-id="acc2c-104">Methods</span></span>  
  
|<span data-ttu-id="acc2c-105">方法</span><span class="sxs-lookup"><span data-stu-id="acc2c-105">Method</span></span>|<span data-ttu-id="acc2c-106">說明</span><span class="sxs-lookup"><span data-stu-id="acc2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acc2c-107">IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="acc2c-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="acc2c-108">取得值，指出是否提供的指標參考的組件清單中。</span><span class="sxs-lookup"><span data-stu-id="acc2c-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="acc2c-109">IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="acc2c-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="acc2c-110">取得值，指出所提供的名稱是否符合清單中的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="acc2c-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc2c-111">備註</span><span class="sxs-lookup"><span data-stu-id="acc2c-111">Remarks</span></span>  
 <span data-ttu-id="acc2c-112">呼叫[iclrassemblyidentitymanager:: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)方法來取得執行個體的指標`ICLRAssemblyReferenceList`。</span><span class="sxs-lookup"><span data-stu-id="acc2c-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acc2c-113">需求</span><span class="sxs-lookup"><span data-stu-id="acc2c-113">Requirements</span></span>  
 <span data-ttu-id="acc2c-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acc2c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acc2c-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="acc2c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="acc2c-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="acc2c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acc2c-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acc2c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc2c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc2c-118">See Also</span></span>  
 [<span data-ttu-id="acc2c-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="acc2c-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="acc2c-120">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="acc2c-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="acc2c-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="acc2c-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
