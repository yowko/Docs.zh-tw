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
ms.openlocfilehash: 090b587ef509795609250914ce8883ad96d28c18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729677"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 介面

擴充 "ICorDebugEval" 以提供泛型型別的支援。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CallParameterizedFunction 方法](icordebugeval2-callparameterizedfunction-method.md)|設定指定 "ICorDebugFunction" 的呼叫，該呼叫可以嵌套在其函式採用型別參數的型別內，或本身可以接受型別參數。|  
|[CreateValueForType 方法](icordebugeval2-createvaluefortype-method.md)|取得指定之類型的新 "ICorDebugValue" 的指標，其初始值為 null 或零。|  
|[NewParameterizedArray 方法](icordebugeval2-newparameterizedarray-method.md)|配置指定元素類型和維度的新陣列。|  
|[NewParameterizedObject 方法](icordebugeval2-newparameterizedobject-method.md)|具現化新的參數化型別物件，並呼叫物件的函式方法。|  
|[NewParameterizedObjectNoConstructor 方法](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|將指定類別的新參數化型別物件具現化，而不嘗試呼叫函式方法|  
|[NewStringWithLength 方法](icordebugeval2-newstringwithlength-method.md)|使用指定的內容，建立指定長度的新字串。|  
|[RudeAbort 方法](icordebugeval2-rudeabort-method.md)|中止目前正在執行的計算 `ICorDebugEval2` 。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
