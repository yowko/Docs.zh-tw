---
title: _EFN_GetManagedExcepStack 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e201b9a350c030da59e2b6ed27f84f570c8e621
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126655"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="384ca-102">_EFN_GetManagedExcepStack 函式</span><span class="sxs-lookup"><span data-stu-id="384ca-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="384ca-103">給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。</span><span class="sxs-lookup"><span data-stu-id="384ca-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="384ca-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="384ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="384ca-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="384ca-106">[in]正在進行偵錯用戶端。</span><span class="sxs-lookup"><span data-stu-id="384ca-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="384ca-107">[in]Managed 的物件指標，衍生自<xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="384ca-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="384ca-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="384ca-108">szStackString</span></span>  
 <span data-ttu-id="384ca-109">[out]傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="384ca-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="384ca-110">[out]字串緩衝區中有可用的字元數。</span><span class="sxs-lookup"><span data-stu-id="384ca-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="384ca-111">備註</span><span class="sxs-lookup"><span data-stu-id="384ca-111">Remarks</span></span>  
 <span data-ttu-id="384ca-112">如果沒有任何 managed 程式碼的執行緒上目前內容中，則函數會傳回 HRESULT SOS_E_NOMANAGEDCODE 0xa0 設備值與 0x1000 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="384ca-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="384ca-113">需求</span><span class="sxs-lookup"><span data-stu-id="384ca-113">Requirements</span></span>  
 <span data-ttu-id="384ca-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="384ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="384ca-115">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="384ca-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="384ca-116">.NET framework 版本：</span><span class="sxs-lookup"><span data-stu-id="384ca-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="384ca-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384ca-117">See also</span></span>

- [<span data-ttu-id="384ca-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="384ca-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
