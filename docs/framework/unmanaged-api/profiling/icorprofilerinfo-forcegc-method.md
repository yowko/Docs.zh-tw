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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 208552dd94f587b9326280ad455ca2478ae4ac4d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780255"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC 方法
強制記憶體回收發生 common language runtime (CLR) 中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>備註  
 `ForceGC`必須呼叫方法，只能從從未執行 managed 程式碼和其堆疊上沒有任何分析工具回呼的執行緒。 最方便的實作會建立個別的執行緒內呼叫程式碼剖析工具`ForceGC`時收到信號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
