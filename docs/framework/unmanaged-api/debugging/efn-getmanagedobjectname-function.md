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
ms.openlocfilehash: 0fb694cf85256c0f3ac5ae179e53ff504ab707e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676201"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="2b7a3-102">\_EFN \_ GetManagedObjectName 函式</span><span class="sxs-lookup"><span data-stu-id="2b7a3-102">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="2b7a3-103">使用提供的 managed 物件指標，取得型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b7a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b7a3-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b7a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b7a3-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="2b7a3-106">在Debug 用戶端的指標。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="2b7a3-107">在Managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="2b7a3-108">szName</span><span class="sxs-lookup"><span data-stu-id="2b7a3-108">szName</span></span>  
 <span data-ttu-id="2b7a3-109">擴展型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="2b7a3-110">擴展字串緩衝區中的可用字元數。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b7a3-111">備註</span><span class="sxs-lookup"><span data-stu-id="2b7a3-111">Remarks</span></span>  

 <span data-ttu-id="2b7a3-112">如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b7a3-113">需求</span><span class="sxs-lookup"><span data-stu-id="2b7a3-113">Requirements</span></span>  

 <span data-ttu-id="2b7a3-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7a3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b7a3-115">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="2b7a3-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="2b7a3-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b7a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7a3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b7a3-117">See also</span></span>

- [<span data-ttu-id="2b7a3-118">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2b7a3-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
