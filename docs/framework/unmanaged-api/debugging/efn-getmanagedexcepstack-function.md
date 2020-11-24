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
ms.openlocfilehash: b86277836b1be48c9f8020d59071aba8c5b1e457
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676227"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="6921d-102">\_EFN \_ GetManagedExcepStack 函式</span><span class="sxs-lookup"><span data-stu-id="6921d-102">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="6921d-103">給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。</span><span class="sxs-lookup"><span data-stu-id="6921d-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6921d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6921d-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6921d-105">參數</span><span class="sxs-lookup"><span data-stu-id="6921d-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="6921d-106">在正在進行調試的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6921d-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="6921d-107">在衍生自的 managed 物件指標 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="6921d-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="6921d-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="6921d-108">szStackString</span></span>  
 <span data-ttu-id="6921d-109">擴展傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="6921d-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="6921d-110">擴展字串緩衝區中的可用字元數。</span><span class="sxs-lookup"><span data-stu-id="6921d-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6921d-111">備註</span><span class="sxs-lookup"><span data-stu-id="6921d-111">Remarks</span></span>  

 <span data-ttu-id="6921d-112">如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。</span><span class="sxs-lookup"><span data-stu-id="6921d-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6921d-113">需求</span><span class="sxs-lookup"><span data-stu-id="6921d-113">Requirements</span></span>  

 <span data-ttu-id="6921d-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6921d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6921d-115">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="6921d-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6921d-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6921d-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6921d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6921d-117">See also</span></span>

- [<span data-ttu-id="6921d-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6921d-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
