---
title: "_EFN_GetManagedObjectName 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectName
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectName
helpviewer_keywords: _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80e36f6c60c4c305cad9176cd7f185d8b6d2fdf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="669d6-102">_EFN_GetManagedObjectName 函式</span><span class="sxs-lookup"><span data-stu-id="669d6-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="669d6-103">取得使用提供的 managed 的物件指標的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="669d6-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="669d6-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="669d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="669d6-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="669d6-106">[in]偵錯用戶端指標。</span><span class="sxs-lookup"><span data-stu-id="669d6-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="669d6-107">[in]Managed 的物件指標。</span><span class="sxs-lookup"><span data-stu-id="669d6-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="669d6-108">szName</span><span class="sxs-lookup"><span data-stu-id="669d6-108">szName</span></span>  
 <span data-ttu-id="669d6-109">[out]型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="669d6-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="669d6-110">[out]在字串緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="669d6-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="669d6-111">備註</span><span class="sxs-lookup"><span data-stu-id="669d6-111">Remarks</span></span>  
 <span data-ttu-id="669d6-112">如果沒有任何 managed 程式碼的執行緒上目前內容中，函數會傳回 HRESULT SOS_E_NOMANAGEDCODE 0xa0 設備值與 0x1000 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="669d6-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669d6-113">需求</span><span class="sxs-lookup"><span data-stu-id="669d6-113">Requirements</span></span>  
 <span data-ttu-id="669d6-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="669d6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669d6-115">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="669d6-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="669d6-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="669d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="669d6-117">See Also</span></span>  
 [<span data-ttu-id="669d6-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="669d6-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
