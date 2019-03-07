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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 675bf2ad36fe5006a44890f8ccd6e6197f264ac1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484468"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="4e375-102">_EFN_GetManagedObjectFieldInfo 函式</span><span class="sxs-lookup"><span data-stu-id="4e375-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="4e375-103">使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。</span><span class="sxs-lookup"><span data-stu-id="4e375-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e375-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e375-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e375-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e375-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="4e375-106">[in]偵錯用戶端指標。</span><span class="sxs-lookup"><span data-stu-id="4e375-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="4e375-107">[in]Managed 的物件指標。</span><span class="sxs-lookup"><span data-stu-id="4e375-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="4e375-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="4e375-108">szFieldName</span></span>  
 <span data-ttu-id="4e375-109">[in]Managed 的物件指標的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="4e375-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="4e375-110">[out]欄位值。</span><span class="sxs-lookup"><span data-stu-id="4e375-110">[out] The field value.</span></span> <span data-ttu-id="4e375-111">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="4e375-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="4e375-112">[out]從位移`objAddr`欄位。</span><span class="sxs-lookup"><span data-stu-id="4e375-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="4e375-113">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="4e375-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e375-114">備註</span><span class="sxs-lookup"><span data-stu-id="4e375-114">Remarks</span></span>  
 <span data-ttu-id="4e375-115">如果位移是 0，不會寫入位移。</span><span class="sxs-lookup"><span data-stu-id="4e375-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="4e375-116">如果沒有任何 managed 程式碼的執行緒上目前內容中，則函數會傳回 HRESULT SOS_E_NOMANAGEDCODE 0xa0 設備值與 0x1000 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4e375-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e375-117">需求</span><span class="sxs-lookup"><span data-stu-id="4e375-117">Requirements</span></span>  
 <span data-ttu-id="4e375-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e375-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e375-119">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="4e375-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="4e375-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e375-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e375-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e375-121">See also</span></span>
- [<span data-ttu-id="4e375-122">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4e375-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
