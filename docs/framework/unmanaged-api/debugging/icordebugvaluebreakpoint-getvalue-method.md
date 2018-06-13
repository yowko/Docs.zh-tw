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
ms.openlocfilehash: b8ff07c483ef1bcbf9d5141b7180cea08454ebef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417095"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="2f5b2-102">ICorDebugValueBreakpoint::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="2f5b2-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="2f5b2-103">取得設定中斷點之物件的值表示 「 ICorDebugValue"物件的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2f5b2-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f5b2-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f5b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f5b2-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="2f5b2-106">[out]位址指標`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="2f5b2-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5b2-107">需求</span><span class="sxs-lookup"><span data-stu-id="2f5b2-107">Requirements</span></span>  
 <span data-ttu-id="2f5b2-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f5b2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5b2-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f5b2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f5b2-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f5b2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f5b2-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5b2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5b2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f5b2-112">See Also</span></span>  
 
