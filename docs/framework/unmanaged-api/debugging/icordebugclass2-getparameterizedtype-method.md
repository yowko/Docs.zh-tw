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
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894049"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType 方法
取得這個類別的類型宣告。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>參數  
 `elementType`  
 在CorElementType 列舉的值，指定這個類別的元素類型：如果此 ICorDebugClass2 代表實數值型別，請將此值設定為 ELEMENT_TYPE_VALUETYPE。 如果這`ICorDebugClass2`代表複雜類型，請將此值設定為 ELEMENT_TYPE_CLASS。  
  
 `nTypeArgs`  
 在型別參數的數目（如果型別是泛型的話）。 類型參數的數目（如果有的話）必須符合類別所需的數目。  
  
 `ppTypeArgs`  
 在指標陣列，其中每一個都會指向代表類型參數的 ICorDebugType 物件。 如果類別為非泛型，則此值為 null。  
  
 `ppType`  
 脫銷代表類型宣告之`ICorDebugType`物件位址的指標。 這個物件相當於 managed 程式<xref:System.Type>代碼中的物件。  
  
## <a name="remarks"></a>備註  
 如果類別是非泛型的，也就是說，如果沒有型別參數， `GetParameterizedType`則只會取得對應至類別的執行時間型別物件。 `elementType`參數應該設定為類別的正確元素類型：如果類別是實數值型別，則為 ELEMENT_TYPE_VALUETYPE。否則，ELEMENT_TYPE_CLASS。  
  
 如果類別接受型別參數（例如`ArrayList<T>`），您可以使用`GetParameterizedType`來針對具現化的型別（例如）來建立`ArrayList<int>`型別物件。  
  
## <a name="background-information"></a>背景資訊  
 在 .NET Framework 版本1.0 和1.1 中，中繼資料中的每個型別都可以直接對應到執行中進程中的型別。 因此，元資料類型和執行時間類型在執行中的進程中具有單一標記法。 不過，中繼資料中的一個泛型型別可以對應到執行中進程中類型的許多不同具現化。 例如，中繼資料`SortedList<K,V>`型別可以對應至`SortedList<String, EmployeeRecord>`、 `SortedList<Int32, String>`、 `SortedList<String,Array<Int32>>`等等。 因此，您需要一種方法來處理類型具現化。  
  
 .NET Framework 版本2.0 引進了`ICorDebugType`介面。 若為泛型型別， `ICorDebugClass`或`ICorDebugClass2`物件代表未具現化的`SortedList<K,V>`型別（） `ICorDebugType` ，而物件代表各種具現化的類型。 假設有`ICorDebugClass`或`ICorDebugClass2`物件，您可以藉由`ICorDebugType`呼叫`ICorDebugClass2::GetParameterizedType`方法來建立任何具現化的物件。 您也可以為簡單`ICorDebugType`的類型（例如 Int32）或非泛型型別建立物件。  
  
 引進`ICorDebugType`物件來表示類型的執行時間概念，會影響整個 API 的 ripple。 先前取得`ICorDebugClass`或`ICorDebugClass2`物件或甚至是`CorElementType`值的函式，會一般化以接受`ICorDebugType`物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
