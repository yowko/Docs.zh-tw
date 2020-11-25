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
ms.openlocfilehash: 85cfd7ba648f21721f1a9689843eac232489cb42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728013"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="e7ff9-102">ICorDebugThread::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="e7ff9-102">ICorDebugThread::GetID Method</span></span>

<span data-ttu-id="e7ff9-103">取得此 ICorDebugThread 之現用部分的目前作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="e7ff9-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ff9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7ff9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7ff9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7ff9-105">Parameters</span></span>  

 `pdwThreadId`  
 <span data-ttu-id="e7ff9-106">擴展執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e7ff9-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7ff9-107">備註</span><span class="sxs-lookup"><span data-stu-id="e7ff9-107">Remarks</span></span>  

 <span data-ttu-id="e7ff9-108">作業系統識別碼可能會在程式執行期間變更，而且可能是執行緒不同部分的不同值。</span><span class="sxs-lookup"><span data-stu-id="e7ff9-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ff9-109">需求</span><span class="sxs-lookup"><span data-stu-id="e7ff9-109">Requirements</span></span>  

 <span data-ttu-id="e7ff9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ff9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ff9-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7ff9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7ff9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ff9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ff9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ff9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
