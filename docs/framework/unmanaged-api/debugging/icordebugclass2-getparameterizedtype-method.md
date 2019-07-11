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
ms.openlocfilehash: 1bfc503bfc2b278d7a7344b94cb089cd8e019890
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747762"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType 方法
取得這個類別的型別宣告。  
  
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
 [in]CorElementType 列舉，指定此類別的項目類型值：如果此 ICorDebugClass2 表示實值型別，則您可以將 ELEMENT_TYPE_VALUETYPE 這個值。 將此值設定 ELEMENT_TYPE_CLASS，如果這個`ICorDebugClass2`代表複雜型別。  
  
 `nTypeArgs`  
 [in]型別參數，如果是泛型類型的數目。 （如果有的話） 的型別參數數目必須符合類別所需的數目。  
  
 `ppTypeArgs`  
 [in]指標的陣列，其中每一個指向 ICorDebugType 物件，表示型別參數。 如果非泛型類別，這個值是 null。  
  
 `ppType`  
 [out]位址指標`ICorDebugType`物件，表示型別宣告。 這個物件是否相當於<xref:System.Type>managed 程式碼中的物件。  
  
## <a name="remarks"></a>備註  
 如果類別為非泛型，也就是如果它沒有類型參數，`GetParameterizedType`只取得對應至類別的執行階段型別物件。 `elementType`參數應該設定為正確的項目類型的類別：如果類別是實值型別;，ELEMENT_TYPE_VALUETYPE否則，ELEMENT_TYPE_CLASS。  
  
 如果類別接受型別參數 (例如`ArrayList<T>`)，您可以使用`GetParameterizedType`這類建構的型別物件具現化類型`ArrayList<int>`。  
  
## <a name="background-information"></a>背景資訊  
 在.NET framework 1.0 和 1.1 版中，中繼資料中的每個型別無法直接對應到執行程序中的類型。 因此，中繼資料類型和執行階段類型，請在執行中處理序中必須為單一表示法。 不過，在中繼資料中的一個泛型型別可以對應至許多不同的具現化執行程序中的型別。 例如，中繼資料型別`SortedList<K,V>`可以對應至`SortedList<String, EmployeeRecord>`， `SortedList<Int32, String>`， `SortedList<String,Array<Int32>>`，依此類推。 因此，您需要處理類型具現化的方法。  
  
 .NET Framework 2.0 版導入了`ICorDebugType`介面。 泛型型別，`ICorDebugClass`或是`ICorDebugClass2`物件表示未具現化的型別 (`SortedList<K,V>`)，和`ICorDebugType`物件都代表不同的具現化的類型。 給定`ICorDebugClass`或是`ICorDebugClass2`物件，您可以建立`ICorDebugType`藉由呼叫任何具現化物件`ICorDebugClass2::GetParameterizedType`方法。 您也可以建立`ICorDebugType`簡單型別，例如 Int32，或非泛型類型的物件。  
  
 引進`ICorDebugType`物件來表示類型的執行階段概念有波及整個 API。 先前需要函式`ICorDebugClass`或`ICorDebugClass2`物件，或甚至`CorElementType`值已經被一般化採取`ICorDebugType`物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
