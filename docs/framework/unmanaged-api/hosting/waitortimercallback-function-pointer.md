---
title: WAITORTIMERCALLBACK 函式指標
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d36ae3ef63c1324f77786ad55674bbdc257d984
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607130"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="095c1-102">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="095c1-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="095c1-103">指向主應用程式等候處理的函式 (<xref:System.Threading.WaitHandle>) 已收到信號或逾時。</span><span class="sxs-lookup"><span data-stu-id="095c1-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="095c1-104">中已被取代此函式指標[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="095c1-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095c1-105">語法</span><span class="sxs-lookup"><span data-stu-id="095c1-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="095c1-106">參數</span><span class="sxs-lookup"><span data-stu-id="095c1-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="095c1-107">[in]物件，包含主機所定義的資訊指標。</span><span class="sxs-lookup"><span data-stu-id="095c1-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="095c1-108">[in]`true`如果逾時等候控制代碼，或`false`，表示收到信號。</span><span class="sxs-lookup"><span data-stu-id="095c1-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="095c1-109">備註</span><span class="sxs-lookup"><span data-stu-id="095c1-109">Remarks</span></span>  
 <span data-ttu-id="095c1-110">函式，其中`WAITORTIMERCALLBACK`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="095c1-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095c1-111">需求</span><span class="sxs-lookup"><span data-stu-id="095c1-111">Requirements</span></span>  
 <span data-ttu-id="095c1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="095c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095c1-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="095c1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="095c1-114">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="095c1-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="095c1-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095c1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="095c1-116">See also</span></span>
- [<span data-ttu-id="095c1-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="095c1-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
