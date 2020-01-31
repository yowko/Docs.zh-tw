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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784161"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass 介面

表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。 如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule 方法](icordebugclass-getmodule-method.md)|取得定義此類別的模組。|  
|[GetStaticFieldValue 方法](icordebugclass-getstaticfieldvalue-method.md)|取得指定靜態欄位的值。|  
|[GetToken 方法](icordebugclass-gettoken-method.md)|取得這個類別的 `TypeDef` 中繼資料 token。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugClass` 介面代表未具現化的泛型型別。 ICorDebugType 介面代表具現化的泛型型別。 例如，`Hashtable<K, V>` 會以 `ICorDebugClass`表示，而 `Hashtable<Int32, String>` 則會以 `ICorDebugType`表示。  
  
 非泛型型別是由 `ICorDebugClass` 和 `ICorDebugType`表示。 第二個介面是在 .NET Framework 版本2.0 中引進，以處理類型具現化。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
