---
title: ICorDebugThread::GetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419626"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="83312-102">ICorDebugThread::GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="83312-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="83312-103">取得這個 ICorDebugThread 物件目前的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="83312-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83312-104">語法</span><span class="sxs-lookup"><span data-stu-id="83312-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83312-105">參數</span><span class="sxs-lookup"><span data-stu-id="83312-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="83312-106">[out]指標的位元組合 CorDebugThreadState 列舉值，描述這個執行緒的目前偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="83312-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83312-107">備註</span><span class="sxs-lookup"><span data-stu-id="83312-107">Remarks</span></span>  
 <span data-ttu-id="83312-108">如果目前已停止處理程序，`pState`代表存在於這個執行緒繼續執行，不實際目前執行緒的狀態這個程序時的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="83312-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83312-109">需求</span><span class="sxs-lookup"><span data-stu-id="83312-109">Requirements</span></span>  
 <span data-ttu-id="83312-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83312-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83312-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83312-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83312-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83312-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83312-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83312-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
