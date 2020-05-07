---
title: ICorDebugClass::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: fd048b692ad05f60621a057024be22cb48b3abbe
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894203"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="458de-102">ICorDebugClass::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="458de-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="458de-103">取得定義此類別的模組。</span><span class="sxs-lookup"><span data-stu-id="458de-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458de-104">語法</span><span class="sxs-lookup"><span data-stu-id="458de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="458de-105">參數</span><span class="sxs-lookup"><span data-stu-id="458de-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="458de-106">脫銷ICorDebugModule 物件位址的指標，表示定義此類別的模組。</span><span class="sxs-lookup"><span data-stu-id="458de-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458de-107">需求</span><span class="sxs-lookup"><span data-stu-id="458de-107">Requirements</span></span>  
 <span data-ttu-id="458de-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="458de-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458de-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458de-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458de-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458de-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
