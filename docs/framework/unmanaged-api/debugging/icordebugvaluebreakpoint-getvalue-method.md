---
title: "ICorDebugValueBreakpoint::GetValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68f918b74a5a4abd9820071b4a4772f9b57b9c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="f99c3-102">ICorDebugValueBreakpoint::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="f99c3-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="f99c3-103">取得設定中斷點之物件的值表示 「 ICorDebugValue"物件的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f99c3-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="f99c3-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f99c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="f99c3-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="f99c3-106">[out]位址指標`ICorDebugValue`物件。</span><span class="sxs-lookup"><span data-stu-id="f99c3-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99c3-107">需求</span><span class="sxs-lookup"><span data-stu-id="f99c3-107">Requirements</span></span>  
 <span data-ttu-id="f99c3-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f99c3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99c3-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f99c3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f99c3-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f99c3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f99c3-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99c3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99c3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f99c3-112">See Also</span></span>  
 
