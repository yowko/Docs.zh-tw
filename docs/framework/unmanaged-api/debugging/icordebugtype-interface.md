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
ms.openlocfilehash: b830af5d59c0eb177d815451ecedbdc14121aaad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964751"
---
# <a name="icordebugtype-interface"></a>ICorDebugType 介面
代表基本或複雜的類型 (也就是使用者定義的)。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|取得參考此<xref:System.Type> `ICorDebugType`所參考類別之泛型參數的 ICorDebugTypeEnum 介面指標。|  
|[GetBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|取得`ICorDebugType`的介面指標, 它會參考這個`ICorDebugType`所參考之類別的基類 (如果有的話)。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|取得參考這個之具型別 (this `ICorDebugType`) 之 ICorDebugClass 的介面指標。|  
|[GetFirstTypeParameter 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|取得的介面指標, 其`ICorDebugType`參考這個`ICorDebugType`所參考之<xref:System.Type>類別的函式的第一個泛型參數。|  
|[GetRank 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|取得陣列類型中的維度數目。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|取得 ICorDebugValue 的介面指標, 其中包含指定之堆疊框架中指定欄位標記所參考的靜態欄位值。|  
|[GetType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|取得 CorElementType 值, 描述這個<xref:System.Type> `ICorDebugType`所參考之通用語言執行時間的原生類型。|  
  
## <a name="remarks"></a>備註  
 如果類型是泛型, `ICorDebugClass`則表示未具現化的類型。 `ICorDebugType`介面表示具現化的泛型型別。 例如, hashtable\<K, V > 會由`ICorDebugClass`表示, 而雜湊表\< `ICorDebugType`Int32, 則字串 > 會以表示。  
  
 非泛型型別是以`ICorDebugClass`和`ICorDebugType`表示。 第二個介面是在 .NET Framework 版本2.0 中引進, 以處理類型具現化。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
