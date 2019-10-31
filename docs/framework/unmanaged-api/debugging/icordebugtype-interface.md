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
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129632"
---
# <a name="icordebugtype-interface"></a>ICorDebugType 介面
代表基本或複雜的類型（也就是使用者定義的）。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|取得參考此 `ICorDebugType`所參考類別之泛型 <xref:System.Type> 參數的 ICorDebugTypeEnum 介面指標。|  
|[GetBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|取得參考此 `ICorDebugType`所參考類別之基類的 `ICorDebugType` 介面指標（如果有的話）。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|取得參考此 `ICorDebugType`之具類型的函式之 ICorDebugClass 的介面指標。|  
|[GetFirstTypeParameter 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|取得 `ICorDebugType` 的介面指標，參考此 `ICorDebugType`所參考之類別的函式的第一個泛型 <xref:System.Type> 參數。|  
|[GetRank 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|取得陣列類型中的維度數目。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|取得 ICorDebugValue 的介面指標，其中包含指定之堆疊框架中指定欄位標記所參考的靜態欄位值。|  
|[GetType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|取得 CorElementType 值，描述此 `ICorDebugType`所參考之 common language runtime <xref:System.Type> 的原生類型。|  
  
## <a name="remarks"></a>備註  
 如果類型是泛型，`ICorDebugClass` 代表未具現化的類型。 `ICorDebugType` 介面代表具現化的泛型型別。 例如，Hashtable\<K，V > 會以 `ICorDebugClass`表示，而雜湊表\<Int32，String > 會以 `ICorDebugType`表示。  
  
 非泛型型別是由 `ICorDebugClass` 和 `ICorDebugType`表示。 第二個介面是在 .NET Framework 版本2.0 中引進，以處理類型具現化。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
