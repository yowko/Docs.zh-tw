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
ms.openlocfilehash: 6a1bbe5674ba11b5ee6033c65f229d698eff15ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420637"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="1b5b5-102">ICorDebugThread::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="1b5b5-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="1b5b5-103">取得此 ICorDebugThread 物件上使用中 （最新的） 框架的介面指標。</span><span class="sxs-lookup"><span data-stu-id="1b5b5-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b5b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b5b5-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b5b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b5b5-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="1b5b5-106">[out]ICorDebugFrame 介面物件，表示框架的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1b5b5-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b5b5-107">備註</span><span class="sxs-lookup"><span data-stu-id="1b5b5-107">Remarks</span></span>  
 <span data-ttu-id="1b5b5-108">`ppFrame`參數為 null，如果沒有畫面格是目前作用中。</span><span class="sxs-lookup"><span data-stu-id="1b5b5-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b5b5-109">需求</span><span class="sxs-lookup"><span data-stu-id="1b5b5-109">Requirements</span></span>  
 <span data-ttu-id="1b5b5-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b5b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b5b5-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b5b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b5b5-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b5b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b5b5-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
