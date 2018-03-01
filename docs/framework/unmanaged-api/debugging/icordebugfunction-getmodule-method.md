---
title: "ICorDebugFunction::GetModule 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59808b2a1de969f7d530a1be4cb500fc32cec33f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="c133f-102">ICorDebugFunction::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="c133f-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="c133f-103">取得定義此函式的模組。</span><span class="sxs-lookup"><span data-stu-id="c133f-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c133f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c133f-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c133f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c133f-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="c133f-106">[out]ICorDebugModule 物件，表示此函式定義所在模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c133f-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c133f-107">需求</span><span class="sxs-lookup"><span data-stu-id="c133f-107">Requirements</span></span>  
 <span data-ttu-id="c133f-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c133f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c133f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c133f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c133f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c133f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c133f-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c133f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
