---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: 4e75b8553ff33946654a6a3b6184f98049c6a6cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126673"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="82ba9-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="82ba9-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="82ba9-103">取得值，指出提供的指標是否參考清單中的元件。</span><span class="sxs-lookup"><span data-stu-id="82ba9-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ba9-104">語法</span><span class="sxs-lookup"><span data-stu-id="82ba9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82ba9-105">參數</span><span class="sxs-lookup"><span data-stu-id="82ba9-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="82ba9-106">在要搜尋之元件的介面指標。</span><span class="sxs-lookup"><span data-stu-id="82ba9-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="82ba9-107">有效值的類型為 `IAssemblyName` 或 `IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="82ba9-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82ba9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="82ba9-108">Return Value</span></span>  
  
|<span data-ttu-id="82ba9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82ba9-109">HRESULT</span></span>|<span data-ttu-id="82ba9-110">描述</span><span class="sxs-lookup"><span data-stu-id="82ba9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82ba9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="82ba9-111">S_OK</span></span>|<span data-ttu-id="82ba9-112">此字串會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="82ba9-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="82ba9-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="82ba9-113">S_FALSE</span></span>|<span data-ttu-id="82ba9-114">此字串不會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="82ba9-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="82ba9-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82ba9-115">E_FAIL</span></span>|<span data-ttu-id="82ba9-116">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="82ba9-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82ba9-117">在方法傳回 E_FAIL 之後，通用語言執行時間就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="82ba9-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="82ba9-118">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="82ba9-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82ba9-119">需求</span><span class="sxs-lookup"><span data-stu-id="82ba9-119">Requirements</span></span>  
 <span data-ttu-id="82ba9-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82ba9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82ba9-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="82ba9-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82ba9-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="82ba9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82ba9-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82ba9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ba9-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="82ba9-124">See also</span></span>

- [<span data-ttu-id="82ba9-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="82ba9-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="82ba9-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="82ba9-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="82ba9-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="82ba9-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="82ba9-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="82ba9-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
