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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6a95a636623f0b4ea75706039194572ecf1bbe0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136197"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="8e1f2-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="8e1f2-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="8e1f2-103">取得值，指出是否在清單中的組件是指提供的指標。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e1f2-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e1f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e1f2-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="8e1f2-106">[in]要搜尋的組件介面指標。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="8e1f2-107">有效的值屬於類型`IAssemblyName`或`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e1f2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e1f2-108">Return Value</span></span>  
  
|<span data-ttu-id="8e1f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e1f2-109">HRESULT</span></span>|<span data-ttu-id="8e1f2-110">描述</span><span class="sxs-lookup"><span data-stu-id="8e1f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e1f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e1f2-111">S_OK</span></span>|<span data-ttu-id="8e1f2-112">字串會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="8e1f2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8e1f2-113">S_FALSE</span></span>|<span data-ttu-id="8e1f2-114">字串不會不會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="8e1f2-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e1f2-115">E_FAIL</span></span>|<span data-ttu-id="8e1f2-116">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e1f2-117">方法會傳回 E_FAIL 之後，就不再可在此程序中使用 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="8e1f2-118">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e1f2-119">需求</span><span class="sxs-lookup"><span data-stu-id="8e1f2-119">Requirements</span></span>  
 <span data-ttu-id="8e1f2-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e1f2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e1f2-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e1f2-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e1f2-122">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8e1f2-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e1f2-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e1f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1f2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1f2-124">See also</span></span>

- [<span data-ttu-id="8e1f2-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="8e1f2-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8e1f2-126">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8e1f2-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8e1f2-127">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8e1f2-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="8e1f2-128">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="8e1f2-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
