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
ms.openlocfilehash: fc74b84bccceb1772bf3642e51ec88c562ce5dce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730706"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="51bd9-102">IManagedObject::GetObjectIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="51bd9-102">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="51bd9-103">取得此 managed 物件的識別。</span><span class="sxs-lookup"><span data-stu-id="51bd9-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51bd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="51bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51bd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="51bd9-105">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="51bd9-106">擴展物件所在進程的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="51bd9-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="51bd9-107">擴展物件之應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="51bd9-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="51bd9-108">擴展COM 傳統 v 資料表中物件索引的指標。</span><span class="sxs-lookup"><span data-stu-id="51bd9-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51bd9-109">備註</span><span class="sxs-lookup"><span data-stu-id="51bd9-109">Remarks</span></span>  

 <span data-ttu-id="51bd9-110">Managed 物件的識別包括進程 GUID、應用程式域識別碼，以及 COM 傳統 v 資料表中的物件索引。</span><span class="sxs-lookup"><span data-stu-id="51bd9-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51bd9-111">需求</span><span class="sxs-lookup"><span data-stu-id="51bd9-111">Requirements</span></span>  

 <span data-ttu-id="51bd9-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51bd9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51bd9-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="51bd9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51bd9-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="51bd9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51bd9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51bd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51bd9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51bd9-116">See also</span></span>

- [<span data-ttu-id="51bd9-117">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="51bd9-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
