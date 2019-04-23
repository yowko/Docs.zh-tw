---
title: IManagedObject::GetObjectIdentity 方法
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d014d2900ea790f84331ed933143513ae9e63f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213489"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="ae7d5-102">IManagedObject::GetObjectIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="ae7d5-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="ae7d5-103">取得此受管理物件識別。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae7d5-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae7d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae7d5-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="ae7d5-106">[out]物件所在的程序的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="ae7d5-107">[out]物件的應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="ae7d5-108">[out]物件的索引，在 COM 傳統 v-table 指標。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7d5-109">備註</span><span class="sxs-lookup"><span data-stu-id="ae7d5-109">Remarks</span></span>  
 <span data-ttu-id="ae7d5-110">受管理物件的身分識別會納入 COM 傳統 v-table 處理序 GUID、 應用程式定義域 ID 和物件的索引。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7d5-111">需求</span><span class="sxs-lookup"><span data-stu-id="ae7d5-111">Requirements</span></span>  
 <span data-ttu-id="ae7d5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae7d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae7d5-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae7d5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae7d5-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ae7d5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae7d5-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae7d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7d5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae7d5-116">See also</span></span>

- [<span data-ttu-id="ae7d5-117">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="ae7d5-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
