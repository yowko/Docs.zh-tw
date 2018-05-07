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
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType 方法
取得這個類別的型別宣告。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `elementType`  
 [in]CorElementType 列舉，指定這個類別的項目類型的值： 如果此 ICorDebugClass2 代表實值類型，將此值設 ELEMENT_TYPE_VALUETYPE。 將此值設 ELEMENT_TYPE_CLASS，如果這個`ICorDebugClass2`代表複雜類型。  
  
 `nTypeArgs`  
 [in]型別參數，如果是泛型類型的數目。 （如果有的話） 的型別參數數目必須符合所需的類別數目。  
  
 `ppTypeArgs`  
 [in]指標的陣列，其中每個指向 ICorDebugType 物件，表示型別參數。 如果類別為非泛型，則這個值會是 null。  
  
 `ppType`  
 [out]位址指標`ICorDebugType`物件，代表類型宣告。 此物件是否等於<xref:System.Type>managed 程式碼中的物件。  
  
## <a name="remarks"></a>備註  
 如果類別為非泛型，也就是，如果它沒有類型參數，`GetParameterizedType`只取得對應至類別的執行階段型別物件。 `elementType`參數應設為正確的項目類別的型別： ELEMENT_TYPE_VALUETYPE 如果類別是實值類型; 否則 ELEMENT_TYPE_CLASS。  
  
 如果類別接受型別參數 (例如， `ArrayList<T>`)，您可以使用`GetParameterizedType`建構具現化類型的型別物件，例如`ArrayList<int>`。  
  
## <a name="background-information"></a>背景資訊  
 在.NET framework 1.0 和 1.1 版中，中繼資料中的每個型別無法直接對應至執行中處理序中的類型。 因此，中繼資料類型和執行階段類型，請在執行中處理序中具有單一表示法。 不過，在中繼資料中的一個泛型類型可以對應至許多不同的具現化執行程序中的型別。 例如，中繼資料型別`SortedList<K,V>`可以對應至`SortedList<String, EmployeeRecord>`， `SortedList<Int32, String>`， `SortedList<String,Array<Int32>>`，依此類推。 因此，您需要處理類型具現化的方法。  
  
 .NET Framework 2.0 版導入了`ICorDebugType`介面。 泛型型別，`ICorDebugClass`或`ICorDebugClass2`物件表示未具現化的類型 (`SortedList<K,V>`)，和`ICorDebugType`物件都代表不同的具現化的類型。 指定`ICorDebugClass`或`ICorDebugClass2`物件，您可以建立`ICorDebugType`藉由呼叫任何具現化物件`ICorDebugClass2::GetParameterizedType`方法。 您也可以建立`ICorDebugType`簡單型別，例如 Int32，或非泛型類型的物件。  
  
 導入`ICorDebugType`物件以代表執行階段概念類型的已產生漣漪效果在整個應用程式開發介面。 先前所花費的函式`ICorDebugClass`或`ICorDebugClass2`物件，或甚至`CorElementType`值已經被一般化採取`ICorDebugType`物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
