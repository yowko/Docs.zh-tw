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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca21911f3d16b79887b9d6d8185f8fab17651321
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093211"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="9230c-102">ICorDebugFunction 介面</span><span class="sxs-lookup"><span data-stu-id="9230c-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="9230c-103">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="9230c-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9230c-104">方法</span><span class="sxs-lookup"><span data-stu-id="9230c-104">Methods</span></span>  
  
|<span data-ttu-id="9230c-105">方法</span><span class="sxs-lookup"><span data-stu-id="9230c-105">Method</span></span>|<span data-ttu-id="9230c-106">描述</span><span class="sxs-lookup"><span data-stu-id="9230c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9230c-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="9230c-108">此函式的開頭建立的中斷點。</span><span class="sxs-lookup"><span data-stu-id="9230c-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="9230c-109">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="9230c-110">取得 ICorDebugClass 物件，表示此函式所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="9230c-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="9230c-111">GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="9230c-112">取得最新的編輯，此函式的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9230c-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="9230c-113">GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="9230c-114">取得此函式中的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9230c-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="9230c-115">GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="9230c-116">取得中繼資料語彙基元區域變數簽章的函式，這由`ICorDebugFunction`執行個體。</span><span class="sxs-lookup"><span data-stu-id="9230c-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="9230c-117">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="9230c-118">取得在其中定義這個函式的模組。</span><span class="sxs-lookup"><span data-stu-id="9230c-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="9230c-119">GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="9230c-120">取得此函式中的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="9230c-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="9230c-121">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="9230c-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="9230c-122">取得此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9230c-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9230c-123">備註</span><span class="sxs-lookup"><span data-stu-id="9230c-123">Remarks</span></span>  
 <span data-ttu-id="9230c-124">`ICorDebugFunction`介面並不代表泛型類型參數的函式。</span><span class="sxs-lookup"><span data-stu-id="9230c-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="9230c-125">例如，`ICorDebugFunction`執行個體代表`Func<T>`而非`Func<string>`。</span><span class="sxs-lookup"><span data-stu-id="9230c-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="9230c-126">呼叫[ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)取得泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="9230c-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="9230c-127">方法的中繼資料語彙基元，之間的關聯性`mdMethodDef`，以及方法的`ICorDebugFunction`物件所相依的函數上是否允許編輯後繼續：</span><span class="sxs-lookup"><span data-stu-id="9230c-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="9230c-128">如果函式上不允許編輯後繼續，之間有一對一的關係`ICorDebugFunction`物件和`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9230c-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="9230c-129">也就是說，函式有一個`ICorDebugFunction`物件和一個`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9230c-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="9230c-130">如果函式允許編輯後繼續，之間存在多對一關聯性`ICorDebugFunction`物件和`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9230c-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="9230c-131">也就是說，函式可能有許多執行個體`ICorDebugFunction`，一個用於每個版本的函式，不過只有一個`mdMethodDef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9230c-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9230c-132">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9230c-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9230c-133">需求</span><span class="sxs-lookup"><span data-stu-id="9230c-133">Requirements</span></span>  
 <span data-ttu-id="9230c-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9230c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9230c-135">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9230c-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9230c-136">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9230c-136">**Library:**  CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9230c-137">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9230c-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9230c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9230c-138">See also</span></span>

- [<span data-ttu-id="9230c-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9230c-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
