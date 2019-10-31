---
title: _EFN_GetManagedObjectFieldInfo 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: b68f24908a5b214d507da8e8a4636a7c55259604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123021"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="06729-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="06729-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="06729-103">使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。</span><span class="sxs-lookup"><span data-stu-id="06729-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06729-104">語法</span><span class="sxs-lookup"><span data-stu-id="06729-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06729-105">參數</span><span class="sxs-lookup"><span data-stu-id="06729-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="06729-106">[in] A pointer to the debug client.</span><span class="sxs-lookup"><span data-stu-id="06729-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="06729-107">[in] A managed object pointer.</span><span class="sxs-lookup"><span data-stu-id="06729-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="06729-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="06729-108">szFieldName</span></span>  
 <span data-ttu-id="06729-109">[in] A managed object pointer to the field name.</span><span class="sxs-lookup"><span data-stu-id="06729-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="06729-110">[out] The field value.</span><span class="sxs-lookup"><span data-stu-id="06729-110">[out] The field value.</span></span> <span data-ttu-id="06729-111">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="06729-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="06729-112">[out] The offset from `objAddr` to the field.</span><span class="sxs-lookup"><span data-stu-id="06729-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="06729-113">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="06729-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06729-114">備註</span><span class="sxs-lookup"><span data-stu-id="06729-114">Remarks</span></span>  
 <span data-ttu-id="06729-115">If the offset is 0, no offset is written.</span><span class="sxs-lookup"><span data-stu-id="06729-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="06729-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span><span class="sxs-lookup"><span data-stu-id="06729-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06729-117">需求</span><span class="sxs-lookup"><span data-stu-id="06729-117">Requirements</span></span>  
 <span data-ttu-id="06729-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06729-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06729-119">**Header:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="06729-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="06729-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06729-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06729-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="06729-121">See also</span></span>

- [<span data-ttu-id="06729-122">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="06729-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
