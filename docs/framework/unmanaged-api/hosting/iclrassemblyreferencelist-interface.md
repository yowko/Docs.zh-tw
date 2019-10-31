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
ms.openlocfilehash: e74d49d71cfee51f8cb99645151aace3d02de0e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126658"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="ffd3b-102">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="ffd3b-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="ffd3b-103">管理通用語言執行時間（CLR）載入的元件清單，而不是由主機所載入。</span><span class="sxs-lookup"><span data-stu-id="ffd3b-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffd3b-104">方法</span><span class="sxs-lookup"><span data-stu-id="ffd3b-104">Methods</span></span>  
  
|<span data-ttu-id="ffd3b-105">方法</span><span class="sxs-lookup"><span data-stu-id="ffd3b-105">Method</span></span>|<span data-ttu-id="ffd3b-106">描述</span><span class="sxs-lookup"><span data-stu-id="ffd3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffd3b-107">IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="ffd3b-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="ffd3b-108">取得值，指出提供的指標是否參考清單中的元件。</span><span class="sxs-lookup"><span data-stu-id="ffd3b-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="ffd3b-109">IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="ffd3b-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="ffd3b-110">取得值，指出提供的名稱是否符合清單中元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffd3b-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffd3b-111">備註</span><span class="sxs-lookup"><span data-stu-id="ffd3b-111">Remarks</span></span>  
 <span data-ttu-id="ffd3b-112">呼叫[ICLRAssemblyIdentityManager：： GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)方法，以取得 `ICLRAssemblyReferenceList`實例的指標。</span><span class="sxs-lookup"><span data-stu-id="ffd3b-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffd3b-113">需求</span><span class="sxs-lookup"><span data-stu-id="ffd3b-113">Requirements</span></span>  
 <span data-ttu-id="ffd3b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffd3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffd3b-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ffd3b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffd3b-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ffd3b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffd3b-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffd3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd3b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ffd3b-118">See also</span></span>

- [<span data-ttu-id="ffd3b-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="ffd3b-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ffd3b-120">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="ffd3b-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="ffd3b-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ffd3b-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
