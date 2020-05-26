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
ms.openlocfilehash: 1b40ed8e107d30c22b4ade25d29376b1b74583d1
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842409"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="40b97-102">IManagedObject::GetObjectIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="40b97-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="40b97-103">取得這個 managed 物件的識別。</span><span class="sxs-lookup"><span data-stu-id="40b97-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b97-104">語法</span><span class="sxs-lookup"><span data-stu-id="40b97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40b97-105">參數</span><span class="sxs-lookup"><span data-stu-id="40b97-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="40b97-106">脫銷物件所在進程 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="40b97-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="40b97-107">脫銷物件之應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="40b97-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="40b97-108">脫銷COM 傳統 v 資料表中物件索引的指標。</span><span class="sxs-lookup"><span data-stu-id="40b97-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40b97-109">備註</span><span class="sxs-lookup"><span data-stu-id="40b97-109">Remarks</span></span>  
 <span data-ttu-id="40b97-110">Managed 物件的身分識別包含進程 GUID、應用程式域識別碼，以及 COM 傳統 v 資料表中物件的索引。</span><span class="sxs-lookup"><span data-stu-id="40b97-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b97-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="40b97-111">Requirements</span></span>  
 <span data-ttu-id="40b97-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40b97-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40b97-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="40b97-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40b97-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="40b97-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40b97-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40b97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b97-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40b97-116">See also</span></span>

- [<span data-ttu-id="40b97-117">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="40b97-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
