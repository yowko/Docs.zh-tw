---
title: "IManagedObject::GetObjectIdentity 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5654865c557e6e004685f66753366d7cb575919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="6786e-102">IManagedObject::GetObjectIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="6786e-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="6786e-103">取得此受管理物件識別。</span><span class="sxs-lookup"><span data-stu-id="6786e-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6786e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6786e-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6786e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6786e-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="6786e-106">[out]物件所在的程序的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="6786e-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="6786e-107">[out]物件的應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="6786e-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="6786e-108">[out]物件的索引，在 COM 傳統 v-table 指標。</span><span class="sxs-lookup"><span data-stu-id="6786e-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6786e-109">備註</span><span class="sxs-lookup"><span data-stu-id="6786e-109">Remarks</span></span>  
 <span data-ttu-id="6786e-110">受管理物件的識別則包括 COM 傳統 v-table 中處理程序的 GUID、 應用程式網域識別碼，以及物件的索引。</span><span class="sxs-lookup"><span data-stu-id="6786e-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6786e-111">需求</span><span class="sxs-lookup"><span data-stu-id="6786e-111">Requirements</span></span>  
 <span data-ttu-id="6786e-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6786e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6786e-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6786e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6786e-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6786e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6786e-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6786e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6786e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6786e-116">See Also</span></span>  
 [<span data-ttu-id="6786e-117">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="6786e-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
