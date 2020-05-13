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
ms.openlocfilehash: a74d32478bc88ee634fa5ff9b61ac2059bc8e302
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379709"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="9b998-102">ICorDebugThread::CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="9b998-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="9b998-103">建立 ICorDebugStepper 物件，允許逐步執行此 ICorDebugThread 的現用框架。</span><span class="sxs-lookup"><span data-stu-id="9b998-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b998-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b998-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b998-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b998-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="9b998-106">脫銷物件位址的指標， `ICorDebugStepper` 允許逐步執行這個執行緒的現用框架。</span><span class="sxs-lookup"><span data-stu-id="9b998-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b998-107">備註</span><span class="sxs-lookup"><span data-stu-id="9b998-107">Remarks</span></span>  
 <span data-ttu-id="9b998-108">使用中的框架可能是非受控碼。</span><span class="sxs-lookup"><span data-stu-id="9b998-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="9b998-109">`ICorDebugStepper`介面必須用來執行實際的逐步執行。</span><span class="sxs-lookup"><span data-stu-id="9b998-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b998-110">需求</span><span class="sxs-lookup"><span data-stu-id="9b998-110">Requirements</span></span>  
 <span data-ttu-id="9b998-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b998-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b998-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b998-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b998-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b998-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b998-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b998-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
