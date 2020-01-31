---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863305"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10：： EnumerateObjectReferences 方法

假設有 ObjectID、callback 和 clientData，會列舉每個物件參考（如果有的話）。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>參數

- `objectId`

  \[in] 要列舉參考的物件。

- `callback`

  中的 \[] 使用物件的參考所呼叫的函式。

- `clientData`

  中的 \[] Profiler 提供的資料，以傳遞至 `callback` 函數。

## <a name="remarks"></a>備註

`EnumerateObjectReferences`方法類似于 [ObjectReferences](icorprofilercallback-objectreferences-method.md), 不同之處在于它會針對分析工具依照需求來進行參考, 而不是預先配置陣列來儲存參考。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo10 介面](icorprofilerinfo10-interface.md)
