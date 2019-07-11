---
title: ICorDebugEval::NewObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e4a09db3cedce7b0ae6049c7e550c0c3e21cc8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753178"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="f821c-102">ICorDebugEval::NewObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="f821c-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="f821c-103">配置新的物件執行個體，指定的類型，而不會嘗試呼叫建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="f821c-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="f821c-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="f821c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f821c-105">使用[ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="f821c-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f821c-106">語法</span><span class="sxs-lookup"><span data-stu-id="f821c-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f821c-107">參數</span><span class="sxs-lookup"><span data-stu-id="f821c-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f821c-108">[in]ICorDebugClass 物件，表示要具現化的物件類型的指標。</span><span class="sxs-lookup"><span data-stu-id="f821c-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f821c-109">需求</span><span class="sxs-lookup"><span data-stu-id="f821c-109">Requirements</span></span>  
 <span data-ttu-id="f821c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f821c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f821c-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f821c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f821c-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f821c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f821c-113">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f821c-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f821c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f821c-114">See also</span></span>

- [<span data-ttu-id="f821c-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="f821c-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
