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
ms.openlocfilehash: 50794e96484432c8b7c203f6b8caa60130068a8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122776"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="49c0a-102">ICorDebugBreakpoint::Activate 方法</span><span class="sxs-lookup"><span data-stu-id="49c0a-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="49c0a-103">設定此 `ICorDebugBreakpoint`的作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="49c0a-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="49c0a-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49c0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="49c0a-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="49c0a-106">在將此值設定為 [`true`]，將狀態指定為 [作用中];否則，請將此值設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="49c0a-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c0a-107">需求</span><span class="sxs-lookup"><span data-stu-id="49c0a-107">Requirements</span></span>  
 <span data-ttu-id="49c0a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49c0a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c0a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49c0a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49c0a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49c0a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c0a-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49c0a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
