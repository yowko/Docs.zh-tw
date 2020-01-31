---
title: ICorProfilerInfo::ForceGC 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: e1fe38419cda328c919f0840d51cf6336919aa60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864189"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC 方法
強制在 common language runtime （CLR）中進行垃圾收集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>備註  
 只能從從未執行 managed 程式碼，且在其堆疊上沒有任何分析工具回呼的執行緒呼叫 `ForceGC` 方法。 最方便的執行方式是在分析工具內建立個別的執行緒，以在收到信號時呼叫 `ForceGC`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
