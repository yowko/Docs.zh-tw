---
title: ICorDebugFunction::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 887d207aea3de9296107c041816606b2f5947406
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124036"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="b760f-102">ICorDebugFunction::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="b760f-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="b760f-103">取得 ICorDebugClass 物件，代表此函式為其成員的類別。</span><span class="sxs-lookup"><span data-stu-id="b760f-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b760f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b760f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b760f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b760f-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="b760f-106">脫銷表示類別之 `ICorDebugClass` 物件的位址指標，如果此函式不是類別的成員，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b760f-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b760f-107">需求</span><span class="sxs-lookup"><span data-stu-id="b760f-107">Requirements</span></span>  
 <span data-ttu-id="b760f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b760f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b760f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b760f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b760f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b760f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b760f-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b760f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
