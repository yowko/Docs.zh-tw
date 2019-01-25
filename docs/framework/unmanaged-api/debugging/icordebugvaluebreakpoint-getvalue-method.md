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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7f0ca805b6f2085498977720cb4cb78dac9afae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652575"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="af4f4-102">ICorDebugValueBreakpoint::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="af4f4-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="af4f4-103">取得"ICorDebugValue 」 物件，表示設定中斷點之物件的值的介面指標。</span><span class="sxs-lookup"><span data-stu-id="af4f4-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="af4f4-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af4f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="af4f4-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="af4f4-106">[out]位址指標`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="af4f4-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af4f4-107">需求</span><span class="sxs-lookup"><span data-stu-id="af4f4-107">Requirements</span></span>  
 <span data-ttu-id="af4f4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af4f4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af4f4-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af4f4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af4f4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af4f4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af4f4-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af4f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4f4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af4f4-112">See also</span></span>

