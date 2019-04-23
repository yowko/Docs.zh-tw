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
ms.openlocfilehash: acdfddd015013215bba9039d871837a60ead1405
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175083"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="58d7c-102">ICorDebugValueBreakpoint::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="58d7c-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="58d7c-103">取得"ICorDebugValue 」 物件，表示設定中斷點之物件的值的介面指標。</span><span class="sxs-lookup"><span data-stu-id="58d7c-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="58d7c-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58d7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="58d7c-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="58d7c-106">[out]位址指標`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="58d7c-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58d7c-107">需求</span><span class="sxs-lookup"><span data-stu-id="58d7c-107">Requirements</span></span>  
 <span data-ttu-id="58d7c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58d7c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58d7c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58d7c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58d7c-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58d7c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58d7c-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58d7c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d7c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58d7c-112">See also</span></span>
