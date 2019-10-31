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
ms.openlocfilehash: 770a9280d27c84b950e00e71328c9b28e61c9e7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084814"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="ec926-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="ec926-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="ec926-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span><span class="sxs-lookup"><span data-stu-id="ec926-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec926-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec926-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec926-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec926-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="ec926-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span><span class="sxs-lookup"><span data-stu-id="ec926-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="ec926-107">[in] The number of type arguments passed.</span><span class="sxs-lookup"><span data-stu-id="ec926-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="ec926-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span><span class="sxs-lookup"><span data-stu-id="ec926-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec926-109">備註</span><span class="sxs-lookup"><span data-stu-id="ec926-109">Remarks</span></span>  
 <span data-ttu-id="ec926-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span><span class="sxs-lookup"><span data-stu-id="ec926-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec926-111">需求</span><span class="sxs-lookup"><span data-stu-id="ec926-111">Requirements</span></span>  
 <span data-ttu-id="ec926-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec926-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec926-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec926-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec926-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec926-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec926-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec926-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
