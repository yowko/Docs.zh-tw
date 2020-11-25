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
ms.openlocfilehash: 5fad8b56b783748e23c8adc4aee0e1bf3450e243
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696124"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="ead40-102">ICorDebugFunction::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="ead40-102">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="ead40-103">取得定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="ead40-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead40-104">語法</span><span class="sxs-lookup"><span data-stu-id="ead40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ead40-105">參數</span><span class="sxs-lookup"><span data-stu-id="ead40-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="ead40-106">擴展ICorDebugModule 物件位址的指標，該物件代表定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="ead40-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead40-107">需求</span><span class="sxs-lookup"><span data-stu-id="ead40-107">Requirements</span></span>  

 <span data-ttu-id="ead40-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ead40-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ead40-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ead40-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ead40-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ead40-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ead40-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead40-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
