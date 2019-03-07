---
title: ICorDebugClass2::GetParameterizedType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475629"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="0847a-102">ICorDebugClass2::GetParameterizedType 方法</span><span class="sxs-lookup"><span data-stu-id="0847a-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="0847a-103">取得這個類別的型別宣告。</span><span class="sxs-lookup"><span data-stu-id="0847a-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0847a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0847a-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0847a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0847a-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="0847a-106">[in]CorElementType 列舉，指定此類別的項目類型值：如果此 ICorDebugClass2 表示實值型別，則您可以將 ELEMENT_TYPE_VALUETYPE 這個值。</span><span class="sxs-lookup"><span data-stu-id="0847a-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="0847a-107">將此值設定 ELEMENT_TYPE_CLASS，如果這個`ICorDebugClass2`代表複雜型別。</span><span class="sxs-lookup"><span data-stu-id="0847a-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="0847a-108">[in]型別參數，如果是泛型類型的數目。</span><span class="sxs-lookup"><span data-stu-id="0847a-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="0847a-109">（如果有的話） 的型別參數數目必須符合類別所需的數目。</span><span class="sxs-lookup"><span data-stu-id="0847a-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="0847a-110">[in]指標的陣列，其中每一個指向 ICorDebugType 物件，表示型別參數。</span><span class="sxs-lookup"><span data-stu-id="0847a-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="0847a-111">如果非泛型類別，這個值是 null。</span><span class="sxs-lookup"><span data-stu-id="0847a-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="0847a-112">[out]位址指標`ICorDebugType`物件，表示型別宣告。</span><span class="sxs-lookup"><span data-stu-id="0847a-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="0847a-113">這個物件是否相當於<xref:System.Type>managed 程式碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="0847a-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0847a-114">備註</span><span class="sxs-lookup"><span data-stu-id="0847a-114">Remarks</span></span>  
 <span data-ttu-id="0847a-115">如果類別為非泛型，也就是如果它沒有類型參數，`GetParameterizedType`只取得對應至類別的執行階段型別物件。</span><span class="sxs-lookup"><span data-stu-id="0847a-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="0847a-116">`elementType`參數應該設定為正確的項目類型的類別：如果類別是實值型別;，ELEMENT_TYPE_VALUETYPE否則，ELEMENT_TYPE_CLASS。</span><span class="sxs-lookup"><span data-stu-id="0847a-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="0847a-117">如果類別接受型別參數 (例如`ArrayList<T>`)，您可以使用`GetParameterizedType`這類建構的型別物件具現化類型`ArrayList<int>`。</span><span class="sxs-lookup"><span data-stu-id="0847a-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="0847a-118">背景資訊</span><span class="sxs-lookup"><span data-stu-id="0847a-118">Background Information</span></span>  
 <span data-ttu-id="0847a-119">在.NET framework 1.0 和 1.1 版中，中繼資料中的每個型別無法直接對應到執行程序中的類型。</span><span class="sxs-lookup"><span data-stu-id="0847a-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="0847a-120">因此，中繼資料類型和執行階段類型，請在執行中處理序中必須為單一表示法。</span><span class="sxs-lookup"><span data-stu-id="0847a-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="0847a-121">不過，在中繼資料中的一個泛型型別可以對應至許多不同的具現化執行程序中的型別。</span><span class="sxs-lookup"><span data-stu-id="0847a-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="0847a-122">例如，中繼資料型別`SortedList<K,V>`可以對應至`SortedList<String, EmployeeRecord>`， `SortedList<Int32, String>`， `SortedList<String,Array<Int32>>`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0847a-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="0847a-123">因此，您需要處理類型具現化的方法。</span><span class="sxs-lookup"><span data-stu-id="0847a-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="0847a-124">.NET Framework 2.0 版導入了`ICorDebugType`介面。</span><span class="sxs-lookup"><span data-stu-id="0847a-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="0847a-125">泛型型別，`ICorDebugClass`或是`ICorDebugClass2`物件表示未具現化的型別 (`SortedList<K,V>`)，和`ICorDebugType`物件都代表不同的具現化的類型。</span><span class="sxs-lookup"><span data-stu-id="0847a-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="0847a-126">給定`ICorDebugClass`或是`ICorDebugClass2`物件，您可以建立`ICorDebugType`藉由呼叫任何具現化物件`ICorDebugClass2::GetParameterizedType`方法。</span><span class="sxs-lookup"><span data-stu-id="0847a-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="0847a-127">您也可以建立`ICorDebugType`簡單型別，例如 Int32，或非泛型類型的物件。</span><span class="sxs-lookup"><span data-stu-id="0847a-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="0847a-128">引進`ICorDebugType`物件來表示類型的執行階段概念有波及整個 API。</span><span class="sxs-lookup"><span data-stu-id="0847a-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="0847a-129">先前需要函式`ICorDebugClass`或`ICorDebugClass2`物件，或甚至`CorElementType`值已經被一般化採取`ICorDebugType`物件。</span><span class="sxs-lookup"><span data-stu-id="0847a-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0847a-130">需求</span><span class="sxs-lookup"><span data-stu-id="0847a-130">Requirements</span></span>  
 <span data-ttu-id="0847a-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0847a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0847a-132">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0847a-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0847a-133">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0847a-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0847a-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0847a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
