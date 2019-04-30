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
ms.openlocfilehash: e4deaa3ab4b14fbd32d45841966cfac9e33b9f31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987066"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="85fe1-102">ICorDebugThread::GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="85fe1-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="85fe1-103">取得此 ICorDebugThread 的目前使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="85fe1-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fe1-104">語法</span><span class="sxs-lookup"><span data-stu-id="85fe1-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85fe1-105">參數</span><span class="sxs-lookup"><span data-stu-id="85fe1-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="85fe1-106">[out]CorDebugUserState 列舉值，描述這個執行緒的目前使用者狀態的位元組合指標。</span><span class="sxs-lookup"><span data-stu-id="85fe1-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85fe1-107">備註</span><span class="sxs-lookup"><span data-stu-id="85fe1-107">Remarks</span></span>  
 <span data-ttu-id="85fe1-108">使用者狀態的執行緒時它由正在進行偵錯的程式會檢查執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="85fe1-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="85fe1-109">執行緒可能會有多個設定的狀態位元。</span><span class="sxs-lookup"><span data-stu-id="85fe1-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85fe1-110">需求</span><span class="sxs-lookup"><span data-stu-id="85fe1-110">Requirements</span></span>  
 <span data-ttu-id="85fe1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85fe1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85fe1-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85fe1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85fe1-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85fe1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85fe1-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85fe1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
