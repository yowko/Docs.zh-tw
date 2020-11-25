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
ms.openlocfilehash: 139181975d16c2cdacec10ed646cfc2b8fb31a20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717990"
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
 在CorElementType 列舉的值，指定這個類別的元素類型：如果這個 ICorDebugClass2 代表實值型別，請將此值設定為 ELEMENT_TYPE_VALUETYPE。 如果這代表複雜型別，請將此值設定為 ELEMENT_TYPE_CLASS `ICorDebugClass2` 。  
  
 `nTypeArgs`  
 在如果類型為泛型，則為型別參數的數目。 如果任何) 必須符合類別所需的數目，則 (類型參數的數目。  
  
 `ppTypeArgs`  
 在指標的陣列，每個指標都會指向代表型別參數的 ICorDebugType 物件。 如果類別為非泛型，則這個值為 null。  
  
 `ppType`  
 擴展代表類型宣告之物件的位址指標 `ICorDebugType` 。 此物件相當於 managed 程式 <xref:System.Type> 代碼中的物件。  
  
## <a name="remarks"></a>備註  

 如果類別為非泛型，亦即，如果沒有型別參數，則只會 `GetParameterizedType` 取得對應至類別的執行時間型別物件。 `elementType`如果類別是實值型別，則應該將參數設定為正確的元素類型：如果類別是實值型別，則為 ELEMENT_TYPE_VALUETYPE，否則為 ELEMENT_TYPE_CLASS。  
  
 如果類別接受型別參數 (例如 `ArrayList<T>`) ，您可以使用來為具現化的型別（例如） `GetParameterizedType` 建立型別物件 `ArrayList<int>` 。  
  
## <a name="background-information"></a>背景資訊  

 在 .NET Framework 1.0 和1.1 版中，中繼資料中的每個型別都可以直接對應至執行中進程中的型別。 因此，元資料類型和執行時間類型在執行中的進程中具有單一標記法。 不過，中繼資料中的一個泛型型別可以對應至執行中進程中類型的許多不同具現化。 例如，元資料類型 `SortedList<K,V>` 可以對應至 `SortedList<String, EmployeeRecord>` 、 `SortedList<Int32, String>` 、 `SortedList<String,Array<Int32>>` 等等。 因此，您需要一種方法來處理型別具現化。  
  
 .NET Framework 2.0 版引進了 `ICorDebugType` 介面。 若為泛型型別， `ICorDebugClass` 或物件代表未具現 `ICorDebugClass2` 化的類型 (`SortedList<K,V>`) ， `ICorDebugType` 而物件代表各種具現化的類型。 指定 `ICorDebugClass` 或 `ICorDebugClass2` 物件之後，您可以藉 `ICorDebugType` 由呼叫方法，為任何具現化建立物件 `ICorDebugClass2::GetParameterizedType` 。 您也可以建立 `ICorDebugType` 簡單類型的物件，例如 Int32 或非泛型型別的物件。  
  
 引入 `ICorDebugType` 物件來代表類型的執行時間概念，在整個 API 中都有 ripple 效果。 先前 `ICorDebugClass` `ICorDebugClass2` 採用或物件或甚至是值的函式 `CorElementType` 會一般化以取得 `ICorDebugType` 物件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
