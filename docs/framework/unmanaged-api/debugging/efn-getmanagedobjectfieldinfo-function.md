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
ms.openlocfilehash: 182424632e4f81dfdf86e87dc6bb2c75c2780fce
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793764"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="42dd4-102">\_EFN\_GetManagedObjectFieldInfo 函式</span><span class="sxs-lookup"><span data-stu-id="42dd4-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="42dd4-103">使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。</span><span class="sxs-lookup"><span data-stu-id="42dd4-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42dd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="42dd4-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42dd4-105">參數</span><span class="sxs-lookup"><span data-stu-id="42dd4-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="42dd4-106">在Debug 用戶端的指標。</span><span class="sxs-lookup"><span data-stu-id="42dd4-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="42dd4-107">在Managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="42dd4-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="42dd4-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="42dd4-108">szFieldName</span></span>  
 <span data-ttu-id="42dd4-109">在功能變數名稱的 managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="42dd4-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="42dd4-110">脫銷域值。</span><span class="sxs-lookup"><span data-stu-id="42dd4-110">[out] The field value.</span></span> <span data-ttu-id="42dd4-111">這個參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="42dd4-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="42dd4-112">脫銷從 `objAddr` 到欄位的位移。</span><span class="sxs-lookup"><span data-stu-id="42dd4-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="42dd4-113">這個參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="42dd4-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42dd4-114">備註</span><span class="sxs-lookup"><span data-stu-id="42dd4-114">Remarks</span></span>  
 <span data-ttu-id="42dd4-115">如果位移為0，則不會寫入位移。</span><span class="sxs-lookup"><span data-stu-id="42dd4-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="42dd4-116">如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE，並將0xa0 的設備值和錯誤碼為0x1000。</span><span class="sxs-lookup"><span data-stu-id="42dd4-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42dd4-117">需求</span><span class="sxs-lookup"><span data-stu-id="42dd4-117">Requirements</span></span>  
 <span data-ttu-id="42dd4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42dd4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42dd4-119">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="42dd4-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="42dd4-120">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42dd4-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42dd4-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="42dd4-121">See also</span></span>

- [<span data-ttu-id="42dd4-122">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="42dd4-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
