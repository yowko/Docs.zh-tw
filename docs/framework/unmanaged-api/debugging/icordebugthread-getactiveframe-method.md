---
title: ICorDebugThread::GetActiveFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390a2c64508bf407296d318a47bfd2972b7ef9d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762558"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="c8fe3-102">ICorDebugThread::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="c8fe3-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="c8fe3-103">取得這個 ICorDebugThread 物件上使用中 （最新的） 框架的介面指標。</span><span class="sxs-lookup"><span data-stu-id="c8fe3-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fe3-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8fe3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8fe3-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8fe3-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c8fe3-106">[out]ICorDebugFrame 介面物件，表示框架的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c8fe3-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8fe3-107">備註</span><span class="sxs-lookup"><span data-stu-id="c8fe3-107">Remarks</span></span>  
 <span data-ttu-id="c8fe3-108">`ppFrame`參數為 null，如果沒有框架目前為使用。</span><span class="sxs-lookup"><span data-stu-id="c8fe3-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8fe3-109">需求</span><span class="sxs-lookup"><span data-stu-id="c8fe3-109">Requirements</span></span>  
 <span data-ttu-id="c8fe3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8fe3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fe3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8fe3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8fe3-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8fe3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8fe3-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fe3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
