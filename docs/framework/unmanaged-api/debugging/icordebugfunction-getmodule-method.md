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
ms.openlocfilehash: 41ad10fecca2ba1831d9e0d1120d3d1be0be92ad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212954"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="0ebbf-102">ICorDebugFunction::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="0ebbf-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="0ebbf-103">取得定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="0ebbf-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebbf-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ebbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ebbf-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ebbf-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="0ebbf-106">脫銷ICorDebugModule 物件位址的指標，表示定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="0ebbf-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebbf-107">需求</span><span class="sxs-lookup"><span data-stu-id="0ebbf-107">Requirements</span></span>  
 <span data-ttu-id="0ebbf-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ebbf-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebbf-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ebbf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebbf-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebbf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebbf-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebbf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
