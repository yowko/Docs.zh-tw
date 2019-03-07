---
title: ICorDebugThread::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 900fece1dd29f73f77b85ff08e4deff1396f8aaf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484507"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="0ffa6-102">ICorDebugThread::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="0ffa6-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="0ffa6-103">取得此 ICorDebugThread 作用中的部份目前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ffa6-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ffa6-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ffa6-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ffa6-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="0ffa6-106">[out]這個執行緒使用中部分的控制代碼 HTHREAD 指標。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ffa6-107">備註</span><span class="sxs-lookup"><span data-stu-id="0ffa6-107">Remarks</span></span>  
 <span data-ttu-id="0ffa6-108">此程序執行，以及可能會因不同部分之執行緒的控制代碼可能會變更。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="0ffa6-109">這個控制代碼是由偵錯 API 所擁有。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="0ffa6-110">偵錯工具應該複製它後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ffa6-111">需求</span><span class="sxs-lookup"><span data-stu-id="0ffa6-111">Requirements</span></span>  
 <span data-ttu-id="0ffa6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ffa6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ffa6-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ffa6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ffa6-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ffa6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ffa6-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ffa6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
