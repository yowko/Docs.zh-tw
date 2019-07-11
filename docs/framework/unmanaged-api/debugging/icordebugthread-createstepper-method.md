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
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771798"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="30271-102">ICorDebugThread::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="30271-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="30271-103">建立可讓您逐步完成每個使用中畫面格的這個 ICorDebugThread ICorDebugStepper 物件。</span><span class="sxs-lookup"><span data-stu-id="30271-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30271-104">語法</span><span class="sxs-lookup"><span data-stu-id="30271-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30271-105">參數</span><span class="sxs-lookup"><span data-stu-id="30271-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="30271-106">[out]位址指標`ICorDebugStepper`物件，可讓您逐步執行此執行緒的使用中畫面格。</span><span class="sxs-lookup"><span data-stu-id="30271-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30271-107">備註</span><span class="sxs-lookup"><span data-stu-id="30271-107">Remarks</span></span>  
 <span data-ttu-id="30271-108">使用中畫面格可能未受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="30271-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="30271-109">`ICorDebugStepper`介面必須用來執行實際的逐步執行。</span><span class="sxs-lookup"><span data-stu-id="30271-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30271-110">需求</span><span class="sxs-lookup"><span data-stu-id="30271-110">Requirements</span></span>  
 <span data-ttu-id="30271-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30271-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30271-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30271-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30271-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30271-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30271-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30271-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
