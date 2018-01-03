---
title: "ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e403cd3a2adfa77bd2faf368a6effdfa42213a76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="b731e-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="b731e-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="b731e-103">取得值，指出是否在清單中的組件參考提供的指標。</span><span class="sxs-lookup"><span data-stu-id="b731e-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b731e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b731e-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b731e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b731e-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b731e-106">[in]要搜尋的組件介面指標。</span><span class="sxs-lookup"><span data-stu-id="b731e-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="b731e-107">有效值為型別的`IAssemblyName`或`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="b731e-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b731e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b731e-108">Return Value</span></span>  
  
|<span data-ttu-id="b731e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b731e-109">HRESULT</span></span>|<span data-ttu-id="b731e-110">描述</span><span class="sxs-lookup"><span data-stu-id="b731e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b731e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b731e-111">S_OK</span></span>|<span data-ttu-id="b731e-112">字串會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="b731e-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="b731e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b731e-113">S_FALSE</span></span>|<span data-ttu-id="b731e-114">字串不在清單中。</span><span class="sxs-lookup"><span data-stu-id="b731e-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="b731e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b731e-115">E_FAIL</span></span>|<span data-ttu-id="b731e-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b731e-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b731e-117">方法會傳回 E_FAIL 之後，就不再可在處理程序中使用通用語言執行平台。</span><span class="sxs-lookup"><span data-stu-id="b731e-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="b731e-118">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b731e-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b731e-119">需求</span><span class="sxs-lookup"><span data-stu-id="b731e-119">Requirements</span></span>  
 <span data-ttu-id="b731e-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b731e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b731e-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b731e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b731e-122">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b731e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b731e-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b731e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b731e-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="b731e-124">See Also</span></span>  
 [<span data-ttu-id="b731e-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="b731e-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b731e-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b731e-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b731e-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b731e-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="b731e-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="b731e-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
