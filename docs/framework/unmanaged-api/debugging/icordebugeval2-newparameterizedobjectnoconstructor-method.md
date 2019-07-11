---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754442"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="a0562-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="a0562-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="a0562-103">產生指定類別的新參數化型的別物件，而不會嘗試呼叫建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="a0562-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0562-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0562-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0562-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0562-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="a0562-106">[in]ICorDebugClass 物件，表示要具現化物件類別的指標。</span><span class="sxs-lookup"><span data-stu-id="a0562-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a0562-107">[in]傳遞的類型引數數目。</span><span class="sxs-lookup"><span data-stu-id="a0562-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a0562-108">[in]指標的陣列，其中每一個指向 ICorDebugType 物件，表示要具現化的物件型別引數。</span><span class="sxs-lookup"><span data-stu-id="a0562-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0562-109">備註</span><span class="sxs-lookup"><span data-stu-id="a0562-109">Remarks</span></span>  
 <span data-ttu-id="a0562-110">`NewParameterizedObjectNoConstructor`方法將會失敗，如果型別引數數目不正確或錯誤類型的類型引數會傳遞。</span><span class="sxs-lookup"><span data-stu-id="a0562-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0562-111">需求</span><span class="sxs-lookup"><span data-stu-id="a0562-111">Requirements</span></span>  
 <span data-ttu-id="a0562-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0562-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0562-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0562-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0562-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0562-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0562-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0562-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
