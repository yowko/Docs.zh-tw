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
ms.openlocfilehash: aa02b4def015d5badfd0003e08bea5289fe58e17
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700180"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a>ICorProfilerCallback::COMClassicVTableDestroyed 方法

通知分析工具，COM interop vtable 已被終結。  
  
> [!NOTE]
> 此回呼很可能永遠不會發生，因為 vtable 的銷毀會非常接近關機。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a>參數

- `wrappedClassId`

  \[in] 建立此 vtable 之類別的識別碼。

- `implementedIID`

  \[in] 類別所執行之介面的識別碼。 如果介面是內部介面，這個值可能是 Null。

- `pVTable`

  \[in] vtable 開頭的指標。

## <a name="remarks"></a>備註  

 分析工具不應該在其實作為此方法的實中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用搶先式垃圾收集。 如果分析工具在此封鎖並嘗試垃圾收集，則執行時間會封鎖，直到回呼傳回為止。  
  
 分析工具在執行此方法時，不應呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [COMClassicVTableCreated 方法](icorprofilercallback-comclassicvtablecreated-method.md)
