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
ms.openlocfilehash: c36dec80b6885b0ee56670b94dbd0b155a9710b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729703"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="79b88-102">ICorDebugEval2::CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="79b88-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>

<span data-ttu-id="79b88-103">設定指定之 ICorDebugFunction 的呼叫，此呼叫可以嵌套在其函式採用參數的類別內 <xref:System.Type> ，或本身可以接受 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="79b88-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b88-104">語法</span><span class="sxs-lookup"><span data-stu-id="79b88-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79b88-105">參數</span><span class="sxs-lookup"><span data-stu-id="79b88-105">Parameters</span></span>  

 `pFunction`  
 <span data-ttu-id="79b88-106">在 `ICorDebugFunction` 物件的指標，代表要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="79b88-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="79b88-107">在函數所採用的引數數目。</span><span class="sxs-lookup"><span data-stu-id="79b88-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="79b88-108">在指標的陣列，每個指標都會指向表示函式引數的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="79b88-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="79b88-109">在函數中傳遞的值數目。</span><span class="sxs-lookup"><span data-stu-id="79b88-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="79b88-110">在指標的陣列，每個指標都會指向表示函式引數中傳遞之值的 ICorDebugValue 物件。</span><span class="sxs-lookup"><span data-stu-id="79b88-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79b88-111">備註</span><span class="sxs-lookup"><span data-stu-id="79b88-111">Remarks</span></span>  

 <span data-ttu-id="79b88-112">`CallParameterizedFunction` 類似于 [ICorDebugEval：： CallFunction](icordebugeval-callfunction-method.md) ，不同之處在于函式可能在具有型別參數的類別內、本身可以採用型別參數或兩者。</span><span class="sxs-lookup"><span data-stu-id="79b88-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="79b88-113">應先為類別指定型別引數，然後為函式提供型別引數。</span><span class="sxs-lookup"><span data-stu-id="79b88-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="79b88-114">如果函式在不同的應用程式域中，就會發生轉換。</span><span class="sxs-lookup"><span data-stu-id="79b88-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="79b88-115">但是，所有型別和值引數都必須在目標應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="79b88-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="79b88-116">函數評估只能在有限的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="79b88-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="79b88-117">如果 `CallParameterizedFunction` 或 `ICorDebugEval::CallFunction` 失敗，傳回的 HRESULT 將會指出失敗的最普遍可能原因。</span><span class="sxs-lookup"><span data-stu-id="79b88-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b88-118">需求</span><span class="sxs-lookup"><span data-stu-id="79b88-118">Requirements</span></span>  

 <span data-ttu-id="79b88-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79b88-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b88-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79b88-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79b88-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79b88-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79b88-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b88-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
