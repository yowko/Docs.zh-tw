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
ms.openlocfilehash: ad7230731775cbc56dd0f1eaed72df19512d3733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432592"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="9a614-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="9a614-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="9a614-103">取得值，指出所提供的名稱是否符合清單中的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a614-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a614-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a614-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a614-105">參數</span><span class="sxs-lookup"><span data-stu-id="9a614-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="9a614-106">[in]要搜尋的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="9a614-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a614-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9a614-107">Return Value</span></span>  
  
|<span data-ttu-id="9a614-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a614-108">HRESULT</span></span>|<span data-ttu-id="9a614-109">描述</span><span class="sxs-lookup"><span data-stu-id="9a614-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a614-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a614-110">S_OK</span></span>|<span data-ttu-id="9a614-111">字串會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="9a614-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="9a614-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9a614-112">S_FALSE</span></span>|<span data-ttu-id="9a614-113">字串不在清單中。</span><span class="sxs-lookup"><span data-stu-id="9a614-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="9a614-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a614-114">E_FAIL</span></span>|<span data-ttu-id="9a614-115">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9a614-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a614-116">方法會傳回 E_FAIL 之後，就不再可在處理程序中使用通用語言執行平台。</span><span class="sxs-lookup"><span data-stu-id="9a614-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="9a614-117">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9a614-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a614-118">需求</span><span class="sxs-lookup"><span data-stu-id="9a614-118">Requirements</span></span>  
 <span data-ttu-id="9a614-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a614-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a614-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a614-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a614-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9a614-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a614-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a614-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a614-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a614-123">See Also</span></span>  
 [<span data-ttu-id="9a614-124">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="9a614-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="9a614-125">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="9a614-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="9a614-126">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9a614-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="9a614-127">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="9a614-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
