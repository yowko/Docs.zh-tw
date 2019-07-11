---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b2860e811a16406a71d7ab8df123f2b32aaf13e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773293"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="1bc9c-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="1bc9c-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="1bc9c-103">取得值，指出提供的名稱是否符合清單中的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bc9c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bc9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bc9c-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="1bc9c-106">[in]要搜尋的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bc9c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bc9c-107">Return Value</span></span>  
  
|<span data-ttu-id="1bc9c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bc9c-108">HRESULT</span></span>|<span data-ttu-id="1bc9c-109">說明</span><span class="sxs-lookup"><span data-stu-id="1bc9c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bc9c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bc9c-110">S_OK</span></span>|<span data-ttu-id="1bc9c-111">字串會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="1bc9c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1bc9c-112">S_FALSE</span></span>|<span data-ttu-id="1bc9c-113">字串不會不會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="1bc9c-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bc9c-114">E_FAIL</span></span>|<span data-ttu-id="1bc9c-115">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bc9c-116">方法會傳回 E_FAIL 之後，就不再可在此程序中使用 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="1bc9c-117">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1bc9c-118">需求</span><span class="sxs-lookup"><span data-stu-id="1bc9c-118">Requirements</span></span>  
 <span data-ttu-id="1bc9c-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc9c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc9c-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1bc9c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bc9c-121">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1bc9c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bc9c-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc9c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc9c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc9c-123">See also</span></span>

- [<span data-ttu-id="1bc9c-124">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="1bc9c-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1bc9c-125">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="1bc9c-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1bc9c-126">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="1bc9c-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="1bc9c-127">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="1bc9c-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
