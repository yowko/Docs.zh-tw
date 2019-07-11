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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7d3325c8aee44849ff1fb7a6cc06a0ed7c2c6f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769097"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="826d9-102">ICorDebugThread::GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="826d9-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="826d9-103">取得此 ICorDebugThread 的目前使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="826d9-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="826d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="826d9-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="826d9-106">[out]CorDebugUserState 列舉值，描述這個執行緒的目前使用者狀態的位元組合指標。</span><span class="sxs-lookup"><span data-stu-id="826d9-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="826d9-107">備註</span><span class="sxs-lookup"><span data-stu-id="826d9-107">Remarks</span></span>  
 <span data-ttu-id="826d9-108">使用者狀態的執行緒時它由正在進行偵錯的程式會檢查執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="826d9-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="826d9-109">執行緒可能會有多個設定的狀態位元。</span><span class="sxs-lookup"><span data-stu-id="826d9-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826d9-110">需求</span><span class="sxs-lookup"><span data-stu-id="826d9-110">Requirements</span></span>  
 <span data-ttu-id="826d9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="826d9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826d9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="826d9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="826d9-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="826d9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="826d9-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826d9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
