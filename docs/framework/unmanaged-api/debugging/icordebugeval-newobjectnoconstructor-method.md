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
ms.openlocfilehash: 3e99cafe39a030a412bf33aeb9d96d5006ca02df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415957"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="61c17-102">ICorDebugEval::NewObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="61c17-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="61c17-103">配置新的物件執行個體指定的類型，而不會嘗試呼叫建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="61c17-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="61c17-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="61c17-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="61c17-105">使用[icordebugeval2:: Newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="61c17-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c17-106">語法</span><span class="sxs-lookup"><span data-stu-id="61c17-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61c17-107">參數</span><span class="sxs-lookup"><span data-stu-id="61c17-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="61c17-108">[in]ICorDebugClass 物件，表示要具現化的物件類型的指標。</span><span class="sxs-lookup"><span data-stu-id="61c17-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61c17-109">需求</span><span class="sxs-lookup"><span data-stu-id="61c17-109">Requirements</span></span>  
 <span data-ttu-id="61c17-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61c17-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61c17-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61c17-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61c17-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61c17-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61c17-113">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="61c17-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c17-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c17-114">See Also</span></span>  
 [<span data-ttu-id="61c17-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="61c17-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
