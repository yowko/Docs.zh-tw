---
title: ICorDebugType 介面
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74863af1096f8600b8095e593c1f3c820c512e9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663852"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="ee6bd-102">ICorDebugType 介面</span><span class="sxs-lookup"><span data-stu-id="ee6bd-102">ICorDebugType Interface</span></span>
<span data-ttu-id="ee6bd-103">表示型別，基本或複雜 （也就是，使用者定義）。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ee6bd-104">如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee6bd-105">方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-105">Methods</span></span>  
  
|<span data-ttu-id="ee6bd-106">方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-106">Method</span></span>|<span data-ttu-id="ee6bd-107">描述</span><span class="sxs-lookup"><span data-stu-id="ee6bd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee6bd-108">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="ee6bd-109">取得的介面指標參考泛型 ICorDebugTypeEnum<xref:System.Type>類別所參考的參數`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ee6bd-110">GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="ee6bd-111">取得的介面指標`ICorDebugType`參考所參考的類別的基底類別`ICorDebugType`，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="ee6bd-112">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="ee6bd-113">取得的介面指標來參考這個型別建構函式 ICorDebugClass `ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ee6bd-114">GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="ee6bd-115">取得的介面指標`ICorDebugType`參考的第一個泛型<xref:System.Type>參數所參考的類別的建構函式`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="ee6bd-116">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="ee6bd-117">取得陣列型別中的維度數目。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="ee6bd-118">GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="ee6bd-119">取得包含指定的欄位所參考的靜態欄位值 ICorDebugValue 的介面指標權杖中指定的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="ee6bd-120">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="ee6bd-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="ee6bd-121">取得描述通用語言執行平台的原生類型 CorElementType 值<xref:System.Type>所參考`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee6bd-122">備註</span><span class="sxs-lookup"><span data-stu-id="ee6bd-122">Remarks</span></span>  
 <span data-ttu-id="ee6bd-123">如果類型是泛型，`ICorDebugClass`表示未具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="ee6bd-124">`ICorDebugType`介面表示未具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="ee6bd-125">例如，雜湊表\<K，V > 會由`ICorDebugClass`，而雜湊表\<Int32，字串 > 會由`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ee6bd-126">非泛型類型都由兩者`ICorDebugClass`和`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="ee6bd-127">處理類型具現化的.NET Framework 2.0 版中引進了第二個介面。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee6bd-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee6bd-129">需求</span><span class="sxs-lookup"><span data-stu-id="ee6bd-129">Requirements</span></span>  
 <span data-ttu-id="ee6bd-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee6bd-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee6bd-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee6bd-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee6bd-132">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee6bd-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee6bd-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee6bd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6bd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee6bd-134">See also</span></span>

- [<span data-ttu-id="ee6bd-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ee6bd-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
