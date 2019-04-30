---
title: ICorDebugThread::CreateStepper 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987181"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="c0d7f-102">ICorDebugThread::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="c0d7f-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="c0d7f-103">建立可讓您逐步完成每個使用中畫面格的這個 ICorDebugThread ICorDebugStepper 物件。</span><span class="sxs-lookup"><span data-stu-id="c0d7f-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0d7f-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0d7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0d7f-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="c0d7f-106">[out]位址指標`ICorDebugStepper`物件，可讓您逐步執行此執行緒的使用中畫面格。</span><span class="sxs-lookup"><span data-stu-id="c0d7f-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0d7f-107">備註</span><span class="sxs-lookup"><span data-stu-id="c0d7f-107">Remarks</span></span>  
 <span data-ttu-id="c0d7f-108">使用中畫面格可能未受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0d7f-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="c0d7f-109">`ICorDebugStepper`介面必須用來執行實際的逐步執行。</span><span class="sxs-lookup"><span data-stu-id="c0d7f-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0d7f-110">需求</span><span class="sxs-lookup"><span data-stu-id="c0d7f-110">Requirements</span></span>  
 <span data-ttu-id="c0d7f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0d7f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0d7f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0d7f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0d7f-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0d7f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0d7f-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0d7f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
