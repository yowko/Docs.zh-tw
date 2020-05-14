---
title: ICorDebugValueBreakpoint::GetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
ms.openlocfilehash: cc4e1a236f429894fe7ec304b9ccfd3bf717c188
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397005"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="be23c-102">ICorDebugValueBreakpoint::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="be23c-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="be23c-103">取得代表設定中斷點之物件值的 "ICorDebugValue" 物件的介面指標。</span><span class="sxs-lookup"><span data-stu-id="be23c-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be23c-104">語法</span><span class="sxs-lookup"><span data-stu-id="be23c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be23c-105">參數</span><span class="sxs-lookup"><span data-stu-id="be23c-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="be23c-106">脫銷物件位址的指標 `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="be23c-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be23c-107">需求</span><span class="sxs-lookup"><span data-stu-id="be23c-107">Requirements</span></span>  
 <span data-ttu-id="be23c-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be23c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be23c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be23c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be23c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be23c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be23c-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be23c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be23c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be23c-112">See also</span></span>
