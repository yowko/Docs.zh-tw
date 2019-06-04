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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a81e78c0a34f766e1598dd27506f62bd3132f348
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490167"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="b0837-102">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="b0837-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="b0837-103">指向主應用程式執行緒已開始執行的函式。</span><span class="sxs-lookup"><span data-stu-id="b0837-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="b0837-104">在.NET Framework 4 中，已被取代此函式指標。</span><span class="sxs-lookup"><span data-stu-id="b0837-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0837-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0837-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0837-106">參數</span><span class="sxs-lookup"><span data-stu-id="b0837-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="b0837-107">[in]已開始執行的程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="b0837-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0837-108">備註</span><span class="sxs-lookup"><span data-stu-id="b0837-108">Remarks</span></span>  
 <span data-ttu-id="b0837-109">函式，其中`LPTHREAD_START_ROUTINE`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="b0837-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0837-110">需求</span><span class="sxs-lookup"><span data-stu-id="b0837-110">Requirements</span></span>  
 <span data-ttu-id="b0837-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0837-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0837-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0837-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0837-113">**LIBRARY:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="b0837-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="b0837-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0837-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0837-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0837-115">See also</span></span>

- [<span data-ttu-id="b0837-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b0837-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
