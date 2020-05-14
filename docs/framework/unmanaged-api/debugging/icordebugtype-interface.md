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
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396695"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="abc77-102">ICorDebugType 介面</span><span class="sxs-lookup"><span data-stu-id="abc77-102">ICorDebugType Interface</span></span>
<span data-ttu-id="abc77-103">代表基本或複雜的類型（也就是使用者定義的）。</span><span class="sxs-lookup"><span data-stu-id="abc77-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="abc77-104">如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="abc77-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abc77-105">方法</span><span class="sxs-lookup"><span data-stu-id="abc77-105">Methods</span></span>  
  
|<span data-ttu-id="abc77-106">方法</span><span class="sxs-lookup"><span data-stu-id="abc77-106">Method</span></span>|<span data-ttu-id="abc77-107">描述</span><span class="sxs-lookup"><span data-stu-id="abc77-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abc77-108">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="abc77-109">取得參考 <xref:System.Type> 此所參考類別之泛型參數的 ICorDebugTypeEnum 介面指標 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="abc77-110">GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="abc77-111">取得的介面指標 `ICorDebugType` ，它會參考這個所參考之類別的基類 `ICorDebugType` （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="abc77-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="abc77-112">GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="abc77-113">取得參考這個之具型別（this）之 ICorDebugClass 的介面指標 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="abc77-114">GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="abc77-115">取得的介面指標，其 `ICorDebugType` 參考這個所參考之類別的函式的第一個泛型 <xref:System.Type> 參數 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="abc77-116">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="abc77-117">取得陣列類型中的維度數目。</span><span class="sxs-lookup"><span data-stu-id="abc77-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="abc77-118">GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="abc77-119">取得 ICorDebugValue 的介面指標，其中包含指定之堆疊框架中指定欄位標記所參考的靜態欄位值。</span><span class="sxs-lookup"><span data-stu-id="abc77-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="abc77-120">GetType 方法</span><span class="sxs-lookup"><span data-stu-id="abc77-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="abc77-121">取得 CorElementType 值，描述這個所參考之通用語言執行時間的原生類型 <xref:System.Type> `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abc77-122">備註</span><span class="sxs-lookup"><span data-stu-id="abc77-122">Remarks</span></span>  
 <span data-ttu-id="abc77-123">如果類型是泛型， `ICorDebugClass` 則表示未具現化的類型。</span><span class="sxs-lookup"><span data-stu-id="abc77-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="abc77-124">`ICorDebugType`介面表示具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="abc77-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="abc77-125">例如，Hashtable \< K，V> 會由表示 `ICorDebugClass` ，而雜湊表 \< Int32，則字串> 會以表示 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="abc77-126">非泛型型別是以 `ICorDebugClass` 和表示 `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="abc77-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="abc77-127">第二個介面是在 .NET Framework 版本2.0 中引進，以處理類型具現化。</span><span class="sxs-lookup"><span data-stu-id="abc77-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abc77-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="abc77-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc77-129">需求</span><span class="sxs-lookup"><span data-stu-id="abc77-129">Requirements</span></span>  
 <span data-ttu-id="abc77-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abc77-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc77-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abc77-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abc77-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abc77-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abc77-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc77-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc77-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="abc77-134">See also</span></span>

- [<span data-ttu-id="abc77-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="abc77-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
