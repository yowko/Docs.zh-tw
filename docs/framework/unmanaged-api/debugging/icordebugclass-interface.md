---
title: ICorDebugClass 介面
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969273"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass 介面

表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|取得定義此類別的模組。|  
|[GetStaticFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|取得指定靜態欄位的值。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|取得這個`TypeDef`類別的元資料標記。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugClass`介面代表未具現化的泛型型別。 ICorDebugType 介面代表具現化的泛型型別。 例如, `Hashtable<K, V>`會`ICorDebugClass`以表示`Hashtable<Int32, String>` ,`ICorDebugType`而會以表示。  
  
 非泛型型別是以`ICorDebugClass`和`ICorDebugType`表示。 第二個介面是在 .NET Framework 版本2.0 中引進, 以處理類型具現化。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
