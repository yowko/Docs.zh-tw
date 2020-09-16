---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540552"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10：： RequestReJITWithInliners 方法

ReJITs 所要求的方法，以及所要求之方法的任何 inliners。

## <a name="syntax"></a>語法

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>參數

- `dwRejitFlags`

  \[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)的位元遮罩。

- `cFunctions`

  \[in] 要重新編譯的函式數目。

- `moduleIds`

  \[in] 指定 `moduleId` (的部分 `module` ，) 組 `methodDef` 識別要重新編譯的函式。

- `methodIds`

  \[in] 指定 `methodId` (的部分 `module` ，) 組 `methodDef` 識別要重新編譯的函式。

## <a name="remarks"></a>備註

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) 不會追蹤任何內嵌的方法。 分析工具預期會封鎖內嵌，或追蹤所有 inliners 的內嵌和呼叫， `RequestReJIT` 以確保已 ReJITted 內嵌方法的每個實例。 這對附加上的 ReJIT 造成問題，因為分析工具不存在來監視內嵌。 您可以呼叫這個方法，以保證一組完整的 inliners 也會 ReJITted。

## <a name="requirements"></a>需求

**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](icorprofilerinfo10-interface.md)
