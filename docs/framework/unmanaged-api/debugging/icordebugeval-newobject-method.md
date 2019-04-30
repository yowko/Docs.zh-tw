---
title: ICorDebugEval::NewObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c2d6a66eca080b480b508afea36c33b3e0aeec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989036"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="ed91c-102">ICorDebugEval::NewObject 方法</span><span class="sxs-lookup"><span data-stu-id="ed91c-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="ed91c-103">配置新的物件執行個體，並呼叫指定的建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="ed91c-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="ed91c-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="ed91c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ed91c-105">使用[ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="ed91c-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed91c-106">語法</span><span class="sxs-lookup"><span data-stu-id="ed91c-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed91c-107">參數</span><span class="sxs-lookup"><span data-stu-id="ed91c-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="ed91c-108">[in]呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="ed91c-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="ed91c-109">[in] `ppArgs` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ed91c-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="ed91c-110">[in]ICorDebugValue 物件陣列，每一個都代表要傳遞至建構函式的引數。</span><span class="sxs-lookup"><span data-stu-id="ed91c-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed91c-111">需求</span><span class="sxs-lookup"><span data-stu-id="ed91c-111">Requirements</span></span>  
 <span data-ttu-id="ed91c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed91c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed91c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed91c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed91c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed91c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed91c-115">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="ed91c-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed91c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed91c-116">See also</span></span>

- [<span data-ttu-id="ed91c-117">NewParameterizedObject 方法</span><span class="sxs-lookup"><span data-stu-id="ed91c-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
