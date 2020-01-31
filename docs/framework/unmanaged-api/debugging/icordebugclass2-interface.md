---
title: ICorDebugClass2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 795e9f4862992d95eeef98a986545cca47d828c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784146"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2 介面

表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。 這個介面會擴充[ICorDebugClass](icordebugclass-interface.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetParameterizedType 方法](icordebugclass2-getparameterizedtype-method.md)|取得這個類別的類型宣告。|  
|[SetJMCStatus 方法](icordebugclass2-setjmcstatus-method.md)|針對這個類別的每個方法，設定一個值，指出此方法是否為使用者定義的程式碼。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugClass 介面](icordebugclass-interface.md)
- [偵錯介面](debugging-interfaces.md)
