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
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732810"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="eba31-102">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="eba31-102">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="eba31-103">指向函式，該函式會通知主機等候控制碼 (<xref:System.Threading.WaitHandle>) 已發出信號或已超時。</span><span class="sxs-lookup"><span data-stu-id="eba31-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="eba31-104">在 .NET Framework 4 中，此函式指標已被取代。</span><span class="sxs-lookup"><span data-stu-id="eba31-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba31-105">語法</span><span class="sxs-lookup"><span data-stu-id="eba31-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eba31-106">參數</span><span class="sxs-lookup"><span data-stu-id="eba31-106">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="eba31-107">在物件的指標，該物件包含主機所定義的資訊。</span><span class="sxs-lookup"><span data-stu-id="eba31-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="eba31-108">[in] `true` 如果等候控制碼超時，或 `false` 已收到信號。</span><span class="sxs-lookup"><span data-stu-id="eba31-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eba31-109">備註</span><span class="sxs-lookup"><span data-stu-id="eba31-109">Remarks</span></span>  

 <span data-ttu-id="eba31-110">指向函式的函式 `WAITORTIMERCALLBACK` 是回呼函式，而且必須由主控應用程式的寫入器實作為。</span><span class="sxs-lookup"><span data-stu-id="eba31-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba31-111">需求</span><span class="sxs-lookup"><span data-stu-id="eba31-111">Requirements</span></span>  

 <span data-ttu-id="eba31-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eba31-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba31-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eba31-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eba31-114">連結 **庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="eba31-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="eba31-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba31-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba31-116">See also</span></span>

- [<span data-ttu-id="eba31-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="eba31-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
