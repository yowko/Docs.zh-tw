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
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008465"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="ff3e4-102">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="ff3e4-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="ff3e4-103">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="ff3e4-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="ff3e4-104">這個函式指標在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="ff3e4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3e4-105">語法</span><span class="sxs-lookup"><span data-stu-id="ff3e4-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff3e4-106">參數</span><span class="sxs-lookup"><span data-stu-id="ff3e4-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="ff3e4-107">在已開始執行之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="ff3e4-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff3e4-108">備註</span><span class="sxs-lookup"><span data-stu-id="ff3e4-108">Remarks</span></span>  
 <span data-ttu-id="ff3e4-109">點的函式 `LPTHREAD_START_ROUTINE` 是回呼函式，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="ff3e4-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3e4-110">需求</span><span class="sxs-lookup"><span data-stu-id="ff3e4-110">Requirements</span></span>  
 <span data-ttu-id="ff3e4-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff3e4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff3e4-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ff3e4-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff3e4-113">連結**庫：** Mscorwks.dll .dll</span><span class="sxs-lookup"><span data-stu-id="ff3e4-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ff3e4-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff3e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3e4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff3e4-115">See also</span></span>

- [<span data-ttu-id="ff3e4-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="ff3e4-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
