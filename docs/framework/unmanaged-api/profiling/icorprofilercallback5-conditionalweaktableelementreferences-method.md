---
title: ICorProfilerCallback5::ConditionalWeakTableElementReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39ce72451f3a375f0cd3adb67a431162fc421a93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041597"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences 方法

識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。

## <a name="syntax"></a>語法

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>參數

`cRootRefs`\
[in] `keyRefIds`、`valueRefIds` 和 `rootIds` 陣列中的項目數。

`keyRefIds`\
[in] 物件 ID 陣列，針對相依性控制代碼配對中的主要項目，各包含一個 `ObjectID`。

`valueRefIds`\
[in] 物件 ID 陣列，針對相依性控制代碼配對中的次要項目，各包含一個 `ObjectID`。 (`keyRefIds[i]`會保留`valueRefIds[i]`保持運作。)

`rootIds`\
[in] `GCHandleID` 值陣列，這些值會指向包含記憶體回收根目錄相關資訊的整數。

`ObjectID` 方法在回呼自己期間所傳回的 `ConditionalWeakTableElementReferences` 值都無效，因為記憶體回收行程可能正在進行將物件從舊位置移至新位置的程序。 因此，分析工具不應嘗試在 `ConditionalWeakTableElementReferences` 呼叫期間檢查物件。 在 `GarbageCollectionFinished` 時，所有物件都已移至其新位置，可能已完成檢查。

## <a name="example"></a>範例

下列程式碼範例示範如何實作[ICorProfilerCallback5](icorprofilercallback5-interface.md)以及使用此方法。

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a>備註

分析工具[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]或更新版本的版本會實作[ICorProfilerCallback5](icorprofilercallback5-interface.md)介面，並記錄所指定的相依性`ConditionalWeakTableElementReferences`方法。 `ICorProfilerCallback5` 提供一組完整的即時所代表的物件之間的相依性`ConditionalWeakTable`項目。 這些相依性和成員欄位所指定的參考[icorprofilercallback:: Objectreferences](icorprofilercallback-objectreferences-method.md)方法讓 managed 分析工具產生的作用中物件的完整物件圖形。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl, CorProf.h

**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback5 介面](icorprofilercallback5-interface.md)