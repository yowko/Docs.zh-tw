---
title: ICorDebugType Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType
helpviewer_keywords: ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 503d0debef2ec1bebd674234051db8101dcb0de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
代表類型，基本或複雜 （亦即，使用者定義）。 如果是泛型類型，則 `ICorDebugType` 表示具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateTypeParameters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|取得的介面指標來參考泛型 ICorDebugTypeEnum<xref:System.Type>參數類別所參考的`ICorDebugType`。|  
|[GetBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|取得的介面指標`ICorDebugType`參考所參考類別的基底類別`ICorDebugType`，如果有的話。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|取得的介面指標來參考這個型別建構函式 ICorDebugClass `ICorDebugType`。|  
|[GetFirstTypeParameter 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|取得的介面指標`ICorDebugType`參考第一個泛型<xref:System.Type>所參考類別的建構函式的參數`ICorDebugType`。|  
|[GetRank 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|取得陣列型別中的維度數目。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|取得包含所指定的欄位參考的靜態欄位的值 ICorDebugValue 的介面指標的指定之堆疊框架中語彙基元。|  
|[GetType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|取得描述通用語言執行平台的原生類型的 CorElementType 值<xref:System.Type>所參考`ICorDebugType`。|  
  
## <a name="remarks"></a>備註  
 如果類型是泛型，`ICorDebugClass`表示未具現化的型別。 `ICorDebugType`介面表示未具現化的泛型型別。 比方說，雜湊表\<K，V > 則表示由`ICorDebugClass`，而雜湊表\<Int32、 字串 > 則表示由`ICorDebugType`。  
  
 非泛型型別都由兩者`ICorDebugClass`和`ICorDebugType`。 處理類型具現化的.NET Framework 2.0 版中引進了第二個介面。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
