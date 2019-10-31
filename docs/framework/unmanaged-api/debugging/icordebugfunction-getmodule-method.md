---
title: ICorDebugFunction::GetModule 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: e49bf6a7db9edb9e5ae489cc0655eea54406643d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137886"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="48e67-102">ICorDebugFunction::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="48e67-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="48e67-103">取得定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="48e67-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e67-104">語法</span><span class="sxs-lookup"><span data-stu-id="48e67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48e67-105">參數</span><span class="sxs-lookup"><span data-stu-id="48e67-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="48e67-106">脫銷ICorDebugModule 物件位址的指標，表示定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="48e67-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e67-107">需求</span><span class="sxs-lookup"><span data-stu-id="48e67-107">Requirements</span></span>  
 <span data-ttu-id="48e67-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48e67-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e67-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48e67-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48e67-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e67-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e67-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e67-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
