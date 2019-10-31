---
title: ICorDebugEval2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: 49c1b97540644fb48509be3bb988c51c5d11fd8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084864"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 介面

擴充 "ICorDebugEval" 以提供泛型型別的支援。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CallParameterizedFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|設定對指定 "ICorDebugFunction" 的呼叫，其可以嵌套在型別中，而此類型的函式會採用型別參數，或者本身可以接受型別參數。|  
|[CreateValueForType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|取得指定類型之新 "ICorDebugValue" 的指標，其初始值為 null 或零。|  
|[NewParameterizedArray 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|配置指定之元素類型和維度的新陣列。|  
|[NewParameterizedObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|具現化新的參數化型別物件，並呼叫物件的函式方法。|  
|[NewParameterizedObjectNoConstructor 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|在不嘗試呼叫函式方法的情況下，具現化指定類別的新參數化型別物件|  
|[NewStringWithLength 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|使用指定的內容，建立指定長度的新字串。|  
|[RudeAbort 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|中止此 `ICorDebugEval2` 目前正在執行的計算。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
