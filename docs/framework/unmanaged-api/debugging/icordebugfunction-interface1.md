---
title: ICorDebugFunction 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213233"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="f47e1-102">ICorDebugFunction 介面</span><span class="sxs-lookup"><span data-stu-id="f47e1-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="f47e1-103">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="f47e1-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f47e1-104">方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-104">Methods</span></span>  
  
|<span data-ttu-id="f47e1-105">方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-105">Method</span></span>|<span data-ttu-id="f47e1-106">描述</span><span class="sxs-lookup"><span data-stu-id="f47e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f47e1-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="f47e1-108">在此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="f47e1-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="f47e1-109">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="f47e1-110">取得 ICorDebugClass 物件，代表此函式為其成員的類別。</span><span class="sxs-lookup"><span data-stu-id="f47e1-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="f47e1-111">GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="f47e1-112">取得對此函式進行之最新編輯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f47e1-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="f47e1-113">GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="f47e1-114">取得此函式的 Microsoft 中繼語言（MSIL）程式碼。</span><span class="sxs-lookup"><span data-stu-id="f47e1-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="f47e1-115">GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="f47e1-116">取得這個實例所表示之函式的區域變數簽章的元資料標記 `ICorDebugFunction` 。</span><span class="sxs-lookup"><span data-stu-id="f47e1-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="f47e1-117">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="f47e1-118">取得定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="f47e1-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="f47e1-119">GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="f47e1-120">取得此函式的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="f47e1-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="f47e1-121">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="f47e1-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="f47e1-122">取得此函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="f47e1-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f47e1-123">備註</span><span class="sxs-lookup"><span data-stu-id="f47e1-123">Remarks</span></span>  
 <span data-ttu-id="f47e1-124">`ICorDebugFunction`介面不代表具有泛型型別參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f47e1-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="f47e1-125">例如， `ICorDebugFunction` 實例會代表， `Func<T>` 而不是 `Func<string>` 。</span><span class="sxs-lookup"><span data-stu-id="f47e1-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="f47e1-126">呼叫[ICorDebugILFrame2：： EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md)以取得泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="f47e1-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="f47e1-127">方法的元資料標記與方法的物件之間的關聯性， `mdMethodDef` `ICorDebugFunction` 取決於函式上是否允許 [編輯後繼續]：</span><span class="sxs-lookup"><span data-stu-id="f47e1-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="f47e1-128">如果函式不允許 [編輯後繼續]，則物件與標記之間會存在一對一關聯性 `ICorDebugFunction` `mdMethodDef` 。</span><span class="sxs-lookup"><span data-stu-id="f47e1-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f47e1-129">也就是，函式有一個 `ICorDebugFunction` 物件和一個 `mdMethodDef` token。</span><span class="sxs-lookup"><span data-stu-id="f47e1-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="f47e1-130">如果允許在函式上進行 [編輯後繼續]，則物件與標記之間會存在多對一關聯性 `ICorDebugFunction` `mdMethodDef` 。</span><span class="sxs-lookup"><span data-stu-id="f47e1-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f47e1-131">也就是說，函式可能有多個實例 `ICorDebugFunction` ，每個函式版本各一個，但只會有一個 `mdMethodDef` token。</span><span class="sxs-lookup"><span data-stu-id="f47e1-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f47e1-132">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f47e1-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f47e1-133">需求</span><span class="sxs-lookup"><span data-stu-id="f47e1-133">Requirements</span></span>  
 <span data-ttu-id="f47e1-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f47e1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47e1-135">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f47e1-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f47e1-136">連結**庫：** Corguids.lib .lib</span><span class="sxs-lookup"><span data-stu-id="f47e1-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="f47e1-137">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f47e1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47e1-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="f47e1-138">See also</span></span>

- [<span data-ttu-id="f47e1-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f47e1-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
