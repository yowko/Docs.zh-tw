---
title: "ICorDebugEval::CallFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72713d81931b53e8d61fb39cee146fd30a59bfcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="0b866-102">ICorDebugEval::CallFunction 方法</span><span class="sxs-lookup"><span data-stu-id="0b866-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="0b866-103">設定指定函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b866-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="0b866-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="0b866-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0b866-105">使用[icordebugeval2:: Callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="0b866-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b866-106">語法</span><span class="sxs-lookup"><span data-stu-id="0b866-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b866-107">參數</span><span class="sxs-lookup"><span data-stu-id="0b866-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="0b866-108">[in]ICorDebugFunction 物件，指定要呼叫的函式指標。</span><span class="sxs-lookup"><span data-stu-id="0b866-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="0b866-109">[in]函式的引數數目。</span><span class="sxs-lookup"><span data-stu-id="0b866-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="0b866-110">[in]指標的陣列，其中每個指向 ICorDebugValue 物件，指定要傳遞至函數的引數。</span><span class="sxs-lookup"><span data-stu-id="0b866-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b866-111">備註</span><span class="sxs-lookup"><span data-stu-id="0b866-111">Remarks</span></span>  
 <span data-ttu-id="0b866-112">如果函式是虛擬的`CallFunction`將執行虛擬分派。</span><span class="sxs-lookup"><span data-stu-id="0b866-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="0b866-113">如果函式不同的應用程式網域中，則會發生轉換，只要所有引數也是應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="0b866-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b866-114">需求</span><span class="sxs-lookup"><span data-stu-id="0b866-114">Requirements</span></span>  
 <span data-ttu-id="0b866-115">**平台：** WindowSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b866-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b866-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b866-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b866-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b866-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b866-118">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="0b866-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b866-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b866-119">See Also</span></span>  
 [<span data-ttu-id="0b866-120">CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="0b866-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
