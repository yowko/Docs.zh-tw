---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866724"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 通知 common language runtime （CLR）程式碼剖析工具計畫要在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中新增的元件參考。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>參數

- `pAssemblyRefInfo`

  [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)結構的指標，為 CLR 提供在執行元件參考關閉行程時，應該考慮之元件參考的相關資訊。
  
## <a name="remarks"></a>備註  
 分析工具會針對其計畫從[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼的 `wszAssemblyPath` 引數中指定的元件來參考的每個目標群組件，呼叫這個方法。 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)介面物件會傳遞至分析工具的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼，以及 `wszAssemblyPath` 引數中的元件路徑和名稱。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerAssemblyReferenceProvider 介面](icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences 方法](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished 方法](icorprofilercallback-moduleloadfinished-method.md)
