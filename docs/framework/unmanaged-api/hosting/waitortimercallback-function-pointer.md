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
ms.openlocfilehash: db6a20dee21b6c8bbd55fa9b52a159a00fe310d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092029"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="0dc24-102">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="0dc24-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="0dc24-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span><span class="sxs-lookup"><span data-stu-id="0dc24-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="0dc24-104">This function pointer has been deprecated in the .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0dc24-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc24-105">語法</span><span class="sxs-lookup"><span data-stu-id="0dc24-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dc24-106">參數</span><span class="sxs-lookup"><span data-stu-id="0dc24-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="0dc24-107">[in] A pointer to an object that contains information defined by the host.</span><span class="sxs-lookup"><span data-stu-id="0dc24-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="0dc24-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span><span class="sxs-lookup"><span data-stu-id="0dc24-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dc24-109">備註</span><span class="sxs-lookup"><span data-stu-id="0dc24-109">Remarks</span></span>  
 <span data-ttu-id="0dc24-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span><span class="sxs-lookup"><span data-stu-id="0dc24-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc24-111">需求</span><span class="sxs-lookup"><span data-stu-id="0dc24-111">Requirements</span></span>  
 <span data-ttu-id="0dc24-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dc24-113">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0dc24-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0dc24-114">**Library:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0dc24-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0dc24-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dc24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc24-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc24-116">See also</span></span>

- [<span data-ttu-id="0dc24-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0dc24-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
