---
title: ICorDebugEval::CallFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976235"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="19583-102">ICorDebugEval::CallFunction 方法</span><span class="sxs-lookup"><span data-stu-id="19583-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="19583-103">設定對指定函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="19583-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="19583-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="19583-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="19583-105">請改用[ICorDebugEval2：： CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="19583-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="19583-106">語法</span><span class="sxs-lookup"><span data-stu-id="19583-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="19583-107">參數</span><span class="sxs-lookup"><span data-stu-id="19583-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="19583-108">在ICorDebugFunction 物件的指標，指定要呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="19583-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="19583-109">在函數的引數數目。</span><span class="sxs-lookup"><span data-stu-id="19583-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="19583-110">在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，以指定要傳遞給函數的引數。</span><span class="sxs-lookup"><span data-stu-id="19583-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="19583-111">備註</span><span class="sxs-lookup"><span data-stu-id="19583-111">Remarks</span></span>

<span data-ttu-id="19583-112">如果函式是虛擬的`CallFunction` ，將會執行虛擬分派。</span><span class="sxs-lookup"><span data-stu-id="19583-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="19583-113">如果函式在不同的應用程式域中，只要所有引數也在該應用程式域中，就會發生轉換。</span><span class="sxs-lookup"><span data-stu-id="19583-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="19583-114">需求</span><span class="sxs-lookup"><span data-stu-id="19583-114">Requirements</span></span>

<span data-ttu-id="19583-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19583-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="19583-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19583-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="19583-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19583-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="19583-118">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="19583-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="19583-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19583-119">See also</span></span>

- [<span data-ttu-id="19583-120">CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="19583-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
