---
title: LPTHREAD_START_ROUTINE 函式指標
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: c6e0c02af93b9df726202f397bbb2afc306f3b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090873"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="0372c-102">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="0372c-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="0372c-103">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="0372c-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="0372c-104">這個函式指標在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="0372c-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0372c-105">語法</span><span class="sxs-lookup"><span data-stu-id="0372c-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0372c-106">參數</span><span class="sxs-lookup"><span data-stu-id="0372c-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="0372c-107">在已開始執行之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="0372c-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0372c-108">備註</span><span class="sxs-lookup"><span data-stu-id="0372c-108">Remarks</span></span>  
 <span data-ttu-id="0372c-109">`LPTHREAD_START_ROUTINE` 點的函式是回呼函式，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="0372c-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0372c-110">需求</span><span class="sxs-lookup"><span data-stu-id="0372c-110">Requirements</span></span>  
 <span data-ttu-id="0372c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0372c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0372c-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0372c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0372c-113">連結**庫：** Mscorwks.dll .dll</span><span class="sxs-lookup"><span data-stu-id="0372c-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0372c-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0372c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0372c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0372c-115">See also</span></span>

- [<span data-ttu-id="0372c-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0372c-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
