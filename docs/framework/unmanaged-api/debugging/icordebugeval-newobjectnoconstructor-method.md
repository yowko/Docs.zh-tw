---
title: "ICorDebugEval::NewObjectNoConstructor 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceb35781d4685e3576470da3b99a6666ba233e19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="3768c-102">ICorDebugEval::NewObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="3768c-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="3768c-103">配置新的物件執行個體指定的類型，而不會嘗試呼叫建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="3768c-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="3768c-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="3768c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3768c-105">使用[icordebugeval2:: Newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="3768c-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3768c-106">語法</span><span class="sxs-lookup"><span data-stu-id="3768c-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3768c-107">參數</span><span class="sxs-lookup"><span data-stu-id="3768c-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="3768c-108">[in]ICorDebugClass 物件，表示要具現化的物件類型的指標。</span><span class="sxs-lookup"><span data-stu-id="3768c-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3768c-109">需求</span><span class="sxs-lookup"><span data-stu-id="3768c-109">Requirements</span></span>  
 <span data-ttu-id="3768c-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3768c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3768c-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3768c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3768c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3768c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3768c-113">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="3768c-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3768c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3768c-114">See Also</span></span>  
 [<span data-ttu-id="3768c-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="3768c-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
