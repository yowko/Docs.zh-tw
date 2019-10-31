---
title: ICorDebugThread::GetUserState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: f3511ff5ee9b9221037c64a5e17d61f6bf52e5f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133428"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="d1a75-102">ICorDebugThread::GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="d1a75-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="d1a75-103">取得此 ICorDebugThread 的目前使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="d1a75-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a75-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1a75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a75-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1a75-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="d1a75-106">脫銷CorDebugUserState 列舉值的位元組合指標，描述這個執行緒目前的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="d1a75-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a75-107">備註</span><span class="sxs-lookup"><span data-stu-id="d1a75-107">Remarks</span></span>  
 <span data-ttu-id="d1a75-108">當正在進行偵錯工具檢查時，執行緒的使用者狀態就是執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="d1a75-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="d1a75-109">執行緒可能會設定多個狀態位。</span><span class="sxs-lookup"><span data-stu-id="d1a75-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a75-110">需求</span><span class="sxs-lookup"><span data-stu-id="d1a75-110">Requirements</span></span>  
 <span data-ttu-id="d1a75-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1a75-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a75-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1a75-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1a75-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1a75-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1a75-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a75-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
