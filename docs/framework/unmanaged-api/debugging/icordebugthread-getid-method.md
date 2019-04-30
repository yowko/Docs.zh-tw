---
title: ICorDebugThread::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8eef616d51febd1b919e0a1936406551f441b98c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987099"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="f86ac-102">ICorDebugThread::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="f86ac-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="f86ac-103">取得目前的作業系統識別項的使用中的這個 ICorDebugThread 部分。</span><span class="sxs-lookup"><span data-stu-id="f86ac-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="f86ac-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f86ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="f86ac-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="f86ac-106">[out]執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f86ac-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86ac-107">備註</span><span class="sxs-lookup"><span data-stu-id="f86ac-107">Remarks</span></span>  
 <span data-ttu-id="f86ac-108">作業系統識別項期間執行的處理序中，有可能變更，而且可以是不同的值不同部分的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f86ac-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86ac-109">需求</span><span class="sxs-lookup"><span data-stu-id="f86ac-109">Requirements</span></span>  
 <span data-ttu-id="f86ac-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f86ac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86ac-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f86ac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f86ac-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f86ac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f86ac-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86ac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
