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
ms.openlocfilehash: cb2ab28824d209dd1eed627600e30e9ddb0d7c7a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125715"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2 介面

表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。 這個介面會擴充[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetParameterizedType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|取得這個類別的類型宣告。|  
|[SetJMCStatus 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|針對這個類別的每個方法，設定一個值，指出此方法是否為使用者定義的程式碼。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugClass 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
