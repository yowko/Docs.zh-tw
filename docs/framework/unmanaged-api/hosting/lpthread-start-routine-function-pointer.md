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
ms.openlocfilehash: c86b65e136869603f93253678108b2ffa9d388e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730054"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="5a4ff-102">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="5a4ff-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="5a4ff-103">指向函式，該函式會通知主機執行緒已開始執行。</span><span class="sxs-lookup"><span data-stu-id="5a4ff-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="5a4ff-104">在 .NET Framework 4 中，此函式指標已被取代。</span><span class="sxs-lookup"><span data-stu-id="5a4ff-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4ff-105">語法</span><span class="sxs-lookup"><span data-stu-id="5a4ff-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4ff-106">參數</span><span class="sxs-lookup"><span data-stu-id="5a4ff-106">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="5a4ff-107">在已開始執行之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="5a4ff-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a4ff-108">備註</span><span class="sxs-lookup"><span data-stu-id="5a4ff-108">Remarks</span></span>  

 <span data-ttu-id="5a4ff-109">指向函式的函式 `LPTHREAD_START_ROUTINE` 是回呼函式，而且必須由主控應用程式的寫入器實作為。</span><span class="sxs-lookup"><span data-stu-id="5a4ff-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4ff-110">需求</span><span class="sxs-lookup"><span data-stu-id="5a4ff-110">Requirements</span></span>  

 <span data-ttu-id="5a4ff-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4ff-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4ff-112">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5a4ff-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a4ff-113">連結 **庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="5a4ff-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5a4ff-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4ff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a4ff-115">See also</span></span>

- [<span data-ttu-id="5a4ff-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="5a4ff-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
