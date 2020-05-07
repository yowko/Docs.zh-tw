---
title: ICorDebugBreakpoint::Activate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 24dc55cc9a49c3602829ca627d584c761b4088ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894740"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="63c0c-102">ICorDebugBreakpoint::Activate 方法</span><span class="sxs-lookup"><span data-stu-id="63c0c-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="63c0c-103">設定這個`ICorDebugBreakpoint`的作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="63c0c-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="63c0c-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63c0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="63c0c-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="63c0c-106">在將此值設定`true`為，以將狀態指定為作用中;否則，請將此值`false`設定為。</span><span class="sxs-lookup"><span data-stu-id="63c0c-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c0c-107">需求</span><span class="sxs-lookup"><span data-stu-id="63c0c-107">Requirements</span></span>  
 <span data-ttu-id="63c0c-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63c0c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c0c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63c0c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c0c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63c0c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c0c-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c0c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
