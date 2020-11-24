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
ms.openlocfilehash: 4c088b7e1096f8b4cad11a3e27b4045e233989ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676214"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="3aa43-102">\_EFN \_ GetManagedObjectFieldInfo 函式</span><span class="sxs-lookup"><span data-stu-id="3aa43-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>

<span data-ttu-id="3aa43-103">使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3aa43-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa43-104">語法</span><span class="sxs-lookup"><span data-stu-id="3aa43-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aa43-105">參數</span><span class="sxs-lookup"><span data-stu-id="3aa43-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="3aa43-106">在Debug 用戶端的指標。</span><span class="sxs-lookup"><span data-stu-id="3aa43-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="3aa43-107">在Managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="3aa43-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="3aa43-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="3aa43-108">szFieldName</span></span>  
 <span data-ttu-id="3aa43-109">在功能變數名稱的 managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="3aa43-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3aa43-110">擴展域值。</span><span class="sxs-lookup"><span data-stu-id="3aa43-110">[out] The field value.</span></span> <span data-ttu-id="3aa43-111">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="3aa43-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="3aa43-112">擴展從 `objAddr` 到欄位的位移。</span><span class="sxs-lookup"><span data-stu-id="3aa43-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="3aa43-113">此參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="3aa43-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa43-114">備註</span><span class="sxs-lookup"><span data-stu-id="3aa43-114">Remarks</span></span>  

 <span data-ttu-id="3aa43-115">如果位移為0，則不會寫入位移。</span><span class="sxs-lookup"><span data-stu-id="3aa43-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="3aa43-116">如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。</span><span class="sxs-lookup"><span data-stu-id="3aa43-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aa43-117">需求</span><span class="sxs-lookup"><span data-stu-id="3aa43-117">Requirements</span></span>  

 <span data-ttu-id="3aa43-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3aa43-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa43-119">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="3aa43-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="3aa43-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa43-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa43-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3aa43-121">See also</span></span>

- [<span data-ttu-id="3aa43-122">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3aa43-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
