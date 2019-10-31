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
ms.openlocfilehash: 48d2af96b50bf77347256b3d5860405e460a09d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133442"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="d5048-102">ICorDebugThread::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="d5048-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="d5048-103">取得此 ICorDebugThread 中使用中部分的目前作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5048-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5048-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5048-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5048-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5048-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="d5048-106">脫銷執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5048-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5048-107">備註</span><span class="sxs-lookup"><span data-stu-id="d5048-107">Remarks</span></span>  
 <span data-ttu-id="d5048-108">作業系統識別碼在執行進程期間可能會變更，而且線上程的不同部分中可能會有不同的值。</span><span class="sxs-lookup"><span data-stu-id="d5048-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5048-109">需求</span><span class="sxs-lookup"><span data-stu-id="d5048-109">Requirements</span></span>  
 <span data-ttu-id="d5048-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5048-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5048-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5048-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5048-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5048-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5048-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5048-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
