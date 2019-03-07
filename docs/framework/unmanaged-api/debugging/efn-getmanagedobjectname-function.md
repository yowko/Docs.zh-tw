---
title: _EFN_GetManagedObjectName 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a9bef248d00cb62de7c93ba837ebc9f135490cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479905"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="ec860-102">_EFN_GetManagedObjectName 函式</span><span class="sxs-lookup"><span data-stu-id="ec860-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="ec860-103">取得使用提供的 managed 的物件的指標類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec860-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec860-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec860-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec860-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec860-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ec860-106">[in]偵錯用戶端指標。</span><span class="sxs-lookup"><span data-stu-id="ec860-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="ec860-107">[in]Managed 的物件指標。</span><span class="sxs-lookup"><span data-stu-id="ec860-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="ec860-108">szName</span><span class="sxs-lookup"><span data-stu-id="ec860-108">szName</span></span>  
 <span data-ttu-id="ec860-109">[out]型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec860-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="ec860-110">[out]字串緩衝區中有可用的字元數。</span><span class="sxs-lookup"><span data-stu-id="ec860-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec860-111">備註</span><span class="sxs-lookup"><span data-stu-id="ec860-111">Remarks</span></span>  
 <span data-ttu-id="ec860-112">如果沒有任何 managed 程式碼的執行緒上目前內容中，則函數會傳回 HRESULT SOS_E_NOMANAGEDCODE 0xa0 設備值與 0x1000 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ec860-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec860-113">需求</span><span class="sxs-lookup"><span data-stu-id="ec860-113">Requirements</span></span>  
 <span data-ttu-id="ec860-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec860-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec860-115">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="ec860-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ec860-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec860-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec860-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec860-117">See also</span></span>
- [<span data-ttu-id="ec860-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ec860-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
