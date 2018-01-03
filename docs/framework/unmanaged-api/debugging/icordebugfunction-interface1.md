---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="f758a-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="f758a-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="f758a-103">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="f758a-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f758a-104">方法</span><span class="sxs-lookup"><span data-stu-id="f758a-104">Methods</span></span>  
  
|<span data-ttu-id="f758a-105">方法</span><span class="sxs-lookup"><span data-stu-id="f758a-105">Method</span></span>|<span data-ttu-id="f758a-106">描述</span><span class="sxs-lookup"><span data-stu-id="f758a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f758a-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="f758a-108">此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="f758a-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="f758a-109">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="f758a-110">取得 ICorDebugClass 物件，表示此函式所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="f758a-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="f758a-111">GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="f758a-112">取得最新的編輯，此函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f758a-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="f758a-113">GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="f758a-114">此函式取得的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f758a-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="f758a-115">GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="f758a-116">取得中繼資料語彙基元所表示的函式的本機變數簽章`ICorDebugFunction`執行個體。</span><span class="sxs-lookup"><span data-stu-id="f758a-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="f758a-117">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="f758a-118">取得定義此函式的模組。</span><span class="sxs-lookup"><span data-stu-id="f758a-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="f758a-119">GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="f758a-120">取得此函式中的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="f758a-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="f758a-121">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="f758a-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="f758a-122">取得此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f758a-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f758a-123">備註</span><span class="sxs-lookup"><span data-stu-id="f758a-123">Remarks</span></span>  
 <span data-ttu-id="f758a-124">`ICorDebugFunction`介面不代表泛型型別參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f758a-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="f758a-125">例如，`ICorDebugFunction`代表執行個體`Func<T>`但不是`Func<string>`。</span><span class="sxs-lookup"><span data-stu-id="f758a-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="f758a-126">呼叫[icordebugilframe2:: Enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)取得泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="f758a-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="f758a-127">方法的中繼資料語彙基元之間的關聯性`mdMethodDef`，和該方法的`ICorDebugFunction`物件所相依的函式上是否允許編輯後繼續：</span><span class="sxs-lookup"><span data-stu-id="f758a-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="f758a-128">如果函式上不允許編輯後繼續，之間有一對一的關聯性`ICorDebugFunction`物件和`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f758a-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f758a-129">也就是說，函式有一個`ICorDebugFunction`物件和一個`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f758a-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="f758a-130">如果函式允許編輯後繼續，多對一關聯性之間有`ICorDebugFunction`物件和`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f758a-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f758a-131">也就是說，函式可能會有許多執行個體`ICorDebugFunction`，一個用於每個版本的函式，但是只有一個`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f758a-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f758a-132">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f758a-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f758a-133">需求</span><span class="sxs-lookup"><span data-stu-id="f758a-133">Requirements</span></span>  
 <span data-ttu-id="f758a-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f758a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f758a-135">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f758a-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f758a-136">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f758a-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="f758a-137">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f758a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f758a-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="f758a-138">See Also</span></span>  
 [<span data-ttu-id="f758a-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f758a-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
