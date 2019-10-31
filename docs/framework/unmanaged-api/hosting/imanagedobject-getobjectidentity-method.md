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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141242"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="d43f7-102">IManagedObject::GetObjectIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="d43f7-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="d43f7-103">取得這個 managed 物件的識別。</span><span class="sxs-lookup"><span data-stu-id="d43f7-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d43f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d43f7-105">參數</span><span class="sxs-lookup"><span data-stu-id="d43f7-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="d43f7-106">脫銷物件所在進程 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="d43f7-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="d43f7-107">脫銷物件之應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="d43f7-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="d43f7-108">脫銷COM 傳統 v 資料表中物件索引的指標。</span><span class="sxs-lookup"><span data-stu-id="d43f7-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d43f7-109">備註</span><span class="sxs-lookup"><span data-stu-id="d43f7-109">Remarks</span></span>  
 <span data-ttu-id="d43f7-110">Managed 物件的身分識別包含進程 GUID、應用程式域識別碼，以及 COM 傳統 v 資料表中物件的索引。</span><span class="sxs-lookup"><span data-stu-id="d43f7-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43f7-111">需求</span><span class="sxs-lookup"><span data-stu-id="d43f7-111">Requirements</span></span>  
 <span data-ttu-id="d43f7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d43f7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43f7-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d43f7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d43f7-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d43f7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d43f7-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43f7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d43f7-116">See also</span></span>

- [<span data-ttu-id="d43f7-117">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="d43f7-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
