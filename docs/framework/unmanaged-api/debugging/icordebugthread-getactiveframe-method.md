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
ms.openlocfilehash: d623893bd77e46832b0bd823ed60c23e4eee29ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133545"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="22b00-102">ICorDebugThread::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="22b00-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="22b00-103">取得此 ICorDebugThread 物件上作用中（最新）框架的介面指標。</span><span class="sxs-lookup"><span data-stu-id="22b00-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22b00-104">語法</span><span class="sxs-lookup"><span data-stu-id="22b00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22b00-105">參數</span><span class="sxs-lookup"><span data-stu-id="22b00-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="22b00-106">脫銷代表框架之 ICorDebugFrame 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="22b00-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22b00-107">備註</span><span class="sxs-lookup"><span data-stu-id="22b00-107">Remarks</span></span>  
 <span data-ttu-id="22b00-108">如果目前沒有使用中的框架，`ppFrame` 參數為 null。</span><span class="sxs-lookup"><span data-stu-id="22b00-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22b00-109">需求</span><span class="sxs-lookup"><span data-stu-id="22b00-109">Requirements</span></span>  
 <span data-ttu-id="22b00-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22b00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22b00-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22b00-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22b00-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22b00-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22b00-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
