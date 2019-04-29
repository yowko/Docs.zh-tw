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
# <a name="icordebugtype-interface"></a>ICorDebugType 介面
表示型別，基本或複雜 （也就是，使用者定義）。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|取得的介面指標參考泛型 ICorDebugTypeEnum<xref:System.Type>類別所參考的參數`ICorDebugType`。|  
|[GetBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|取得的介面指標`ICorDebugType`參考所參考的類別的基底類別`ICorDebugType`，如果有的話。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|取得的介面指標來參考這個型別建構函式 ICorDebugClass `ICorDebugType`。|  
|[GetFirstTypeParameter 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|取得的介面指標`ICorDebugType`參考的第一個泛型<xref:System.Type>參數所參考的類別的建構函式`ICorDebugType`。|  
|[GetRank 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|取得陣列型別中的維度數目。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|取得包含指定的欄位所參考的靜態欄位值 ICorDebugValue 的介面指標權杖中指定的堆疊框架。|  
|[GetType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|取得描述通用語言執行平台的原生類型 CorElementType 值<xref:System.Type>所參考`ICorDebugType`。|  
  
## <a name="remarks"></a>備註  
 如果類型是泛型，`ICorDebugClass`表示未具現化的型別。 `ICorDebugType`介面表示未具現化的泛型型別。 例如，雜湊表\<K，V > 會由`ICorDebugClass`，而雜湊表\<Int32，字串 > 會由`ICorDebugType`。  
  
 非泛型類型都由兩者`ICorDebugClass`和`ICorDebugType`。 處理類型具現化的.NET Framework 2.0 版中引進了第二個介面。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
