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
ms.openlocfilehash: 7a089831c39c36b0f8a0c7746e95a96e4ddfc5d9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209392"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="983b4-102">ICorDebugFunction::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="983b4-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="983b4-103">取得 ICorDebugClass 物件，代表此函式為其成員的類別。</span><span class="sxs-lookup"><span data-stu-id="983b4-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="983b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="983b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="983b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="983b4-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="983b4-106">脫銷表示類別之物件位址的指標 `ICorDebugClass` ，如果此函式不是類別的成員，則為 null。</span><span class="sxs-lookup"><span data-stu-id="983b4-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="983b4-107">需求</span><span class="sxs-lookup"><span data-stu-id="983b4-107">Requirements</span></span>  
 <span data-ttu-id="983b4-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="983b4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="983b4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="983b4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="983b4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="983b4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="983b4-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="983b4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
