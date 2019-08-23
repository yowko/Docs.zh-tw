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
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917197"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="85f7f-102">ICorDebugFunction 介面</span><span class="sxs-lookup"><span data-stu-id="85f7f-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="85f7f-103">表示 Managed 函式或方法。</span><span class="sxs-lookup"><span data-stu-id="85f7f-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85f7f-104">方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-104">Methods</span></span>  
  
|<span data-ttu-id="85f7f-105">方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-105">Method</span></span>|<span data-ttu-id="85f7f-106">描述</span><span class="sxs-lookup"><span data-stu-id="85f7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85f7f-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="85f7f-108">在此函式的開頭建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="85f7f-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="85f7f-109">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="85f7f-110">取得 ICorDebugClass 物件, 代表此函式為其成員的類別。</span><span class="sxs-lookup"><span data-stu-id="85f7f-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="85f7f-111">GetCurrentVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="85f7f-112">取得對此函式進行之最新編輯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="85f7f-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="85f7f-113">GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="85f7f-114">取得此函式的 Microsoft 中繼語言 (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="85f7f-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="85f7f-115">GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="85f7f-116">取得這個`ICorDebugFunction`實例所表示之函式的區域變數簽章的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="85f7f-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="85f7f-117">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="85f7f-118">取得定義此函數的模組。</span><span class="sxs-lookup"><span data-stu-id="85f7f-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="85f7f-119">GetNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="85f7f-120">取得此函式的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="85f7f-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="85f7f-121">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="85f7f-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="85f7f-122">取得此函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="85f7f-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f7f-123">備註</span><span class="sxs-lookup"><span data-stu-id="85f7f-123">Remarks</span></span>  
 <span data-ttu-id="85f7f-124">`ICorDebugFunction`介面不代表具有泛型型別參數的函式。</span><span class="sxs-lookup"><span data-stu-id="85f7f-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="85f7f-125">例如, 實例會`ICorDebugFunction`代表`Func<T>` , 而不`Func<string>`是。</span><span class="sxs-lookup"><span data-stu-id="85f7f-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="85f7f-126">呼叫[ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)以取得泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="85f7f-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="85f7f-127">方法的元資料標記`mdMethodDef`與方法的`ICorDebugFunction`物件之間的關聯性, 取決於函式上是否允許 [編輯後繼續]:</span><span class="sxs-lookup"><span data-stu-id="85f7f-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="85f7f-128">如果函式不允許 [編輯後繼續], 則`ICorDebugFunction`物件`mdMethodDef`與標記之間會存在一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="85f7f-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="85f7f-129">也就是, 函式有`ICorDebugFunction`一個物件和`mdMethodDef`一個 token。</span><span class="sxs-lookup"><span data-stu-id="85f7f-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="85f7f-130">如果允許在函式上進行 [編輯後繼續], 則`ICorDebugFunction`物件`mdMethodDef`與標記之間會存在多對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="85f7f-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="85f7f-131">也就是說, 函式可能有多個實例`ICorDebugFunction`, 每個函式版本各一個, 但只會有一個`mdMethodDef` token。</span><span class="sxs-lookup"><span data-stu-id="85f7f-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85f7f-132">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="85f7f-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f7f-133">需求</span><span class="sxs-lookup"><span data-stu-id="85f7f-133">Requirements</span></span>  
 <span data-ttu-id="85f7f-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85f7f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f7f-135">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85f7f-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85f7f-136">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85f7f-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f7f-137">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f7f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f7f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f7f-138">See also</span></span>

- [<span data-ttu-id="85f7f-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="85f7f-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
