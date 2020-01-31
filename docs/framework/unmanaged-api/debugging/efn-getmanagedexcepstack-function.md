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
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789156"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="e4211-102">\_EFN\_GetManagedExcepStack 函式</span><span class="sxs-lookup"><span data-stu-id="e4211-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="e4211-103">給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。</span><span class="sxs-lookup"><span data-stu-id="e4211-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4211-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4211-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4211-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4211-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="e4211-106">在正在進行調試的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e4211-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="e4211-107">在Managed 物件指標，衍生自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="e4211-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="e4211-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="e4211-108">szStackString</span></span>  
 <span data-ttu-id="e4211-109">脫銷傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e4211-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="e4211-110">脫銷字串緩衝區中可用的字元數。</span><span class="sxs-lookup"><span data-stu-id="e4211-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4211-111">備註</span><span class="sxs-lookup"><span data-stu-id="e4211-111">Remarks</span></span>  
 <span data-ttu-id="e4211-112">如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE，並將0xa0 的設備值和錯誤碼為0x1000。</span><span class="sxs-lookup"><span data-stu-id="e4211-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4211-113">需求</span><span class="sxs-lookup"><span data-stu-id="e4211-113">Requirements</span></span>  
 <span data-ttu-id="e4211-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4211-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4211-115">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="e4211-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="e4211-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4211-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4211-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4211-117">See also</span></span>

- [<span data-ttu-id="e4211-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e4211-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
