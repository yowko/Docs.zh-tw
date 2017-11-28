---
title: "ICorDebugFunction::CreateBreakpoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68501943e1ac32cd39a3cdc674935c1c5705f911
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="d69dc-102">ICorDebugFunction::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="d69dc-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="d69dc-103">此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="d69dc-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d69dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="d69dc-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d69dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="d69dc-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="d69dc-106">[out]ICorDebugFunctionBreakpoint 物件，表示新的中斷點函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d69dc-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d69dc-107">需求</span><span class="sxs-lookup"><span data-stu-id="d69dc-107">Requirements</span></span>  
 <span data-ttu-id="d69dc-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d69dc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d69dc-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d69dc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d69dc-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d69dc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d69dc-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d69dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
