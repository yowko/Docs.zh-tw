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
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133458"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="53381-102">ICorDebugThread::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="53381-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="53381-103">取得此 ICorDebugThread 之使用中部分的目前控制碼。</span><span class="sxs-lookup"><span data-stu-id="53381-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53381-104">語法</span><span class="sxs-lookup"><span data-stu-id="53381-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53381-105">參數</span><span class="sxs-lookup"><span data-stu-id="53381-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="53381-106">脫銷HTHREAD 的指標，這是這個執行緒之作用中部分的控制碼。</span><span class="sxs-lookup"><span data-stu-id="53381-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53381-107">備註</span><span class="sxs-lookup"><span data-stu-id="53381-107">Remarks</span></span>  
 <span data-ttu-id="53381-108">控制碼可能會在進程執行時變更，而且可能會因為執行緒的不同部分而有所不同。</span><span class="sxs-lookup"><span data-stu-id="53381-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="53381-109">這個控制碼是由偵錯工具 API 所擁有。</span><span class="sxs-lookup"><span data-stu-id="53381-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="53381-110">偵錯工具在使用它之前，應該先複製它。</span><span class="sxs-lookup"><span data-stu-id="53381-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53381-111">需求</span><span class="sxs-lookup"><span data-stu-id="53381-111">Requirements</span></span>  
 <span data-ttu-id="53381-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53381-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53381-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53381-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53381-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53381-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53381-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53381-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
