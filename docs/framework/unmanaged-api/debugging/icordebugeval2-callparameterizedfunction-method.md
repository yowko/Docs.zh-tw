---
title: ICorDebugEval2::CallParameterizedFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: ab31ab8f83a71372c8e12b460458a26996f65ff5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782980"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="30e5a-102">ICorDebugEval2::CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="30e5a-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="30e5a-103">設定對指定 ICorDebugFunction 的呼叫，其可以嵌套在類別中，其會使用 <xref:System.Type> 參數，或者自己可以接受 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="30e5a-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="30e5a-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30e5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="30e5a-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="30e5a-106">在`ICorDebugFunction` 物件的指標，表示要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="30e5a-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="30e5a-107">在函式所採用的引數數目。</span><span class="sxs-lookup"><span data-stu-id="30e5a-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="30e5a-108">在指標陣列，其中每一個都會指向代表函式引數的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="30e5a-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="30e5a-109">在函數中傳遞的值數目。</span><span class="sxs-lookup"><span data-stu-id="30e5a-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="30e5a-110">在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，代表在函數引數中傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="30e5a-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e5a-111">備註</span><span class="sxs-lookup"><span data-stu-id="30e5a-111">Remarks</span></span>  
 <span data-ttu-id="30e5a-112">`CallParameterizedFunction` 類似[ICorDebugEval：： CallFunction](icordebugeval-callfunction-method.md) ，但函式可能位於具有型別參數的類別中，本身可能會採用型別參數，或兩者都是。</span><span class="sxs-lookup"><span data-stu-id="30e5a-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="30e5a-113">應該先為類別指定類型引數，然後為函式提供。</span><span class="sxs-lookup"><span data-stu-id="30e5a-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="30e5a-114">如果函式在不同的應用程式域中，將會發生轉換。</span><span class="sxs-lookup"><span data-stu-id="30e5a-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="30e5a-115">不過，所有類型和值引數都必須在目標應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="30e5a-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="30e5a-116">函數評估只能在有限的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="30e5a-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="30e5a-117">如果 `CallParameterizedFunction` 或 `ICorDebugEval::CallFunction` 失敗，則傳回的 HRESULT 會指出失敗的最常見可能原因。</span><span class="sxs-lookup"><span data-stu-id="30e5a-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e5a-118">需求</span><span class="sxs-lookup"><span data-stu-id="30e5a-118">Requirements</span></span>  
 <span data-ttu-id="30e5a-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30e5a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e5a-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30e5a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30e5a-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30e5a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30e5a-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30e5a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
