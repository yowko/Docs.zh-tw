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
ms.openlocfilehash: 9407dda7aab337f667cd5043b562d0eac94f0f04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711919"
---
# <a name="icordebugtype-interface"></a>ICorDebugType 介面

代表型別，也就是「基本」或「複雜 (」，也就是使用者定義的) 。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](icordebugtype-enumeratetypeparameters-method.md)|取得 ICorDebugTypeEnum 的介面指標，該指標參考這個所 <xref:System.Type> 參考之類別的泛型參數 `ICorDebugType` 。|  
|[GetBase 方法](icordebugtype-getbase-method.md)|取得的介面指標， `ICorDebugType` 該指標會參考這個所參考之類別的基類 `ICorDebugType` （如果有的話）。|  
|[GetClass 方法](icordebugtype-getclass-method.md)|取得 ICorDebugClass 的介面指標，該參考會參考此的具類型的函式 `ICorDebugType` 。|  
|[GetFirstTypeParameter 方法](icordebugtype-getfirsttypeparameter-method.md)|取得的介面指標 `ICorDebugType` ，該指標會參考這個所參考之類別的函式的第一個泛型 <xref:System.Type> 參數 `ICorDebugType` 。|  
|[GetRank 方法](icordebugtype-getrank-method.md)|取得陣列類型中的維度數目。|  
|[GetStaticFieldValue 方法](icordebugtype-getstaticfieldvalue-method.md)|取得 ICorDebugValue 的介面指標，其中包含指定之堆疊框架中指定之欄位標記所參考的靜態欄位值。|  
|[GetType 方法](icordebugtype-gettype-method.md)|取得 CorElementType 值，這個值會描述這個所參考之 common language runtime 的原生類型 <xref:System.Type> `ICorDebugType` 。|  
  
## <a name="remarks"></a>備註  

 如果類型為泛型，則表示未具現化 `ICorDebugClass` 的類型。 `ICorDebugType`介面代表具現化的泛型型別。 例如，雜湊表會以 \<K, V> 表示 `ICorDebugClass` ，而雜湊表 \<Int32, String> 則是以表示 `ICorDebugType` 。  
  
 非泛型型別是由 `ICorDebugClass` 和表示 `ICorDebugType` 。 第二個介面是在 .NET Framework 版本2.0 中引進，以處理型別具現化。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
