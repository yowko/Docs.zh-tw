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
ms.openlocfilehash: 06ff8f0f13d7710d2d3d59aac4b5fdcadfe707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418388"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="85cdd-102">ICorDebugThread::GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="85cdd-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="85cdd-103">取得此 ICorDebugThread 的目前使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="85cdd-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85cdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="85cdd-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85cdd-105">參數</span><span class="sxs-lookup"><span data-stu-id="85cdd-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="85cdd-106">[out]CorDebugUserState 列舉值，描述這個執行緒的目前使用者狀態的位元組合指標。</span><span class="sxs-lookup"><span data-stu-id="85cdd-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85cdd-107">備註</span><span class="sxs-lookup"><span data-stu-id="85cdd-107">Remarks</span></span>  
 <span data-ttu-id="85cdd-108">執行緒的使用者狀態時進行檢查的程式進行偵錯執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="85cdd-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="85cdd-109">執行緒可能會有多個設定的狀態位元。</span><span class="sxs-lookup"><span data-stu-id="85cdd-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85cdd-110">需求</span><span class="sxs-lookup"><span data-stu-id="85cdd-110">Requirements</span></span>  
 <span data-ttu-id="85cdd-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85cdd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85cdd-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85cdd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85cdd-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85cdd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85cdd-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85cdd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
