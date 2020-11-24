---
title: ICorProfilerCallback::ObjectAllocated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674318"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated 方法

通知分析工具，堆積內的記憶體已配置給物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>參數  

 `objectId`  
 在配置記憶體之物件的識別碼。  
  
 `classId`  
 在物件是實例之類別的識別碼。  
  
## <a name="remarks"></a>備註  

 `ObjectedAllocated`從堆疊或非受控記憶體進行配置時，不會呼叫此方法。 `classId`參數可以參考尚未載入之 managed 程式碼中的類別。 分析工具會在回呼之後立即接收該類別的類別載入回呼 `ObjectAllocated` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ClassLoadStarted 方法](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished 方法](icorprofilercallback-classloadfinished-method.md)
