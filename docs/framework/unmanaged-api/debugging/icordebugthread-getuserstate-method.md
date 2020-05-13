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
ms.openlocfilehash: d1ff3427feb5dc8395bbb2fda78e3e93e1a1a8f0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378850"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="22825-102">ICorDebugThread::GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="22825-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="22825-103">取得此 ICorDebugThread 的目前使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="22825-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22825-104">語法</span><span class="sxs-lookup"><span data-stu-id="22825-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22825-105">參數</span><span class="sxs-lookup"><span data-stu-id="22825-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="22825-106">脫銷CorDebugUserState 列舉值的位元組合指標，描述這個執行緒目前的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="22825-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22825-107">備註</span><span class="sxs-lookup"><span data-stu-id="22825-107">Remarks</span></span>  
 <span data-ttu-id="22825-108">當正在進行偵錯工具檢查時，執行緒的使用者狀態就是執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="22825-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="22825-109">執行緒可能會設定多個狀態位。</span><span class="sxs-lookup"><span data-stu-id="22825-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22825-110">需求</span><span class="sxs-lookup"><span data-stu-id="22825-110">Requirements</span></span>  
 <span data-ttu-id="22825-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22825-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22825-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22825-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22825-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22825-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22825-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22825-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
