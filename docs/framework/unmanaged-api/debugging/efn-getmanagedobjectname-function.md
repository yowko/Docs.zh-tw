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
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122997"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="5f4fa-102">\_EFN\_GetManagedObjectName 函式</span><span class="sxs-lookup"><span data-stu-id="5f4fa-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="5f4fa-103">使用提供的 managed 物件指標，取得型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f4fa-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f4fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f4fa-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="5f4fa-106">在Debug 用戶端的指標。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="5f4fa-107">在Managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="5f4fa-108">szName</span><span class="sxs-lookup"><span data-stu-id="5f4fa-108">szName</span></span>  
 <span data-ttu-id="5f4fa-109">脫銷類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="5f4fa-110">脫銷字串緩衝區中可用的字元數。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f4fa-111">備註</span><span class="sxs-lookup"><span data-stu-id="5f4fa-111">Remarks</span></span>  
 <span data-ttu-id="5f4fa-112">如果目前在內容中的執行緒上沒有 managed 程式碼，則函式會傳回具有設備值0xa0 的 HRESULT SOS_E_NOMANAGEDCODE，以及錯誤碼為0x1000。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4fa-113">需求</span><span class="sxs-lookup"><span data-stu-id="5f4fa-113">Requirements</span></span>  
 <span data-ttu-id="5f4fa-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f4fa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f4fa-115">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="5f4fa-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="5f4fa-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f4fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4fa-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f4fa-117">See also</span></span>

- [<span data-ttu-id="5f4fa-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="5f4fa-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
