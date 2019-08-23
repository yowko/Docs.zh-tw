---
title: ICorProfilerCallback::COMClassicVTableDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f74e06ea4cb4d7a8eace8c7852f487bbdcbcd875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964632"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a>ICorProfilerCallback::COMClassicVTableDestroyed 方法
通知分析工具, COM Interop 的 vtable 已終結。  
  
> [!NOTE]
> 此回呼可能永遠不會發生, 因為 vtable 的銷毀會非常接近關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a>參數  
 `wrappedClassId`  
 在建立此 vtable 之類別的識別碼。  
  
 `implementedIID`  
 在類別所實作為介面的識別碼。 如果介面僅供內部用, 這個值可能會是 Null。  
  
 `pVTable`  
 在Vtable 開頭的指標。  
  
## <a name="remarks"></a>備註  
 分析工具不應在此方法的執行中封鎖, 因為堆疊可能不是處於允許垃圾收集的狀態, 因此無法啟用「搶先垃圾收集」。 如果分析工具在此處封鎖並嘗試垃圾收集, 執行時間將會封鎖, 直到這個回呼傳回為止。  
  
 分析工具的此方法的執行不應呼叫 managed 程式碼, 或以任何方式進行, 以造成 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [COMClassicVTableCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
