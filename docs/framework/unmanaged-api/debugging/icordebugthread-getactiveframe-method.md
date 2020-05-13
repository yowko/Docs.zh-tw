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
ms.openlocfilehash: 843c6df1ef41fdd3227b92275182432ad4cc43b1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379733"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="f3267-102">ICorDebugThread::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="f3267-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="f3267-103">取得此 ICorDebugThread 物件上作用中（最新）框架的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f3267-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3267-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3267-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3267-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3267-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="f3267-106">脫銷代表框架之 ICorDebugFrame 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f3267-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3267-107">備註</span><span class="sxs-lookup"><span data-stu-id="f3267-107">Remarks</span></span>  
 <span data-ttu-id="f3267-108">`ppFrame`如果沒有框架目前為使用中，則參數為 null。</span><span class="sxs-lookup"><span data-stu-id="f3267-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3267-109">需求</span><span class="sxs-lookup"><span data-stu-id="f3267-109">Requirements</span></span>  
 <span data-ttu-id="f3267-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3267-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3267-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3267-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3267-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3267-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3267-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3267-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
