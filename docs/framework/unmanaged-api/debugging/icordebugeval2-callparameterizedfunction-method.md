---
title: "ICorDebugEval2::CallParameterizedFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CallParameterizedFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 720d9c4fb9b997538ee2bb18ac7987350f6bfb57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="d4cd6-102">ICorDebugEval2::CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="d4cd6-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="d4cd6-103">設定指定 ICorDebugFunction，可以巢狀的類別的建構函式會採用內部呼叫<xref:System.Type>參數或本身可以採取<xref:System.Type>參數。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4cd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4cd6-104">Syntax</span></span>  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4cd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4cd6-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="d4cd6-106">[in]指標`ICorDebugFunction`物件，代表要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="d4cd6-107">[in]函式的引數數目。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="d4cd6-108">[in]指標的陣列，其中每個指向 ICorDebugType 物件，表示函式引數。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="d4cd6-109">[in]函式中，傳遞的值數目。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="d4cd6-110">[in]指標陣列，其中每個指向 ICorDebugValue 物件，表示值傳入函式引數。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4cd6-111">備註</span><span class="sxs-lookup"><span data-stu-id="d4cd6-111">Remarks</span></span>  
 <span data-ttu-id="d4cd6-112">`CallParameterizedFunction`就像[icordebugeval:: Callfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)不同之處在於函式可能具有型別參數的類別內，可能本身需要型別參數，或兩者。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="d4cd6-113">針對類別，然後再針對函式，應該先指定型別引數。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="d4cd6-114">如果函式是在不同的應用程式網域中，則會發生轉換。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="d4cd6-115">不過，所有類型和值的引數必須都是目標應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="d4cd6-116">只在少數情況下，可以執行函式評估。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="d4cd6-117">如果`CallParameterizedFunction`或`ICorDebugEval::CallFunction`失敗，傳回的 HRESULT 會指出失敗最常見的可能原因。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4cd6-118">需求</span><span class="sxs-lookup"><span data-stu-id="d4cd6-118">Requirements</span></span>  
 <span data-ttu-id="d4cd6-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4cd6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4cd6-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4cd6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4cd6-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4cd6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4cd6-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4cd6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
