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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cefe84c482df3b20b5939e031ad76647f295d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995609"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="902fd-102">ICorDebugFunction::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="902fd-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="902fd-103">取得在其中定義這個函式的模組。</span><span class="sxs-lookup"><span data-stu-id="902fd-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="902fd-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="902fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="902fd-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="902fd-106">[out]ICorDebugModule 物件，表示此函式定義所在模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="902fd-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="902fd-107">需求</span><span class="sxs-lookup"><span data-stu-id="902fd-107">Requirements</span></span>  
 <span data-ttu-id="902fd-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="902fd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902fd-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="902fd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="902fd-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="902fd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="902fd-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
