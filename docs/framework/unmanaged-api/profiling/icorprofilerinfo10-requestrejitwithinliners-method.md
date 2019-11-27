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
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449813"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10：： RequestReJITWithInliners 方法

ReJITs 要求的方法，以及所要求之方法的任何 inliners。

## <a name="syntax"></a>語法

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a>參數

`dwRejitFlags` \
在[COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)的位元遮罩。

`cFunctions` \
[in] 要重新編譯的函式數目。

`moduleIds` \
[in] 指定 (`moduleId`, `module`) 組的 `methodDef` 部分，這個部分可識別所要重新編譯的函式。

`methodIds` \
[in] 指定 (`methodId`, `module`) 組的 `methodDef` 部分，這個部分可識別所要重新編譯的函式。

## <a name="remarks"></a>備註

[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)不會對內嵌的方法進行任何追蹤。 分析工具預期會封鎖內嵌或追蹤內嵌，並為所有 inliners 呼叫 `RequestReJIT`，以確保內嵌方法的每個實例都已 ReJITted。 這會造成 ReJIT on attach 的問題，因為分析工具不存在來監視內嵌。 您可以呼叫這個方法，以確保一組完整的 inliners 也會 ReJITted。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
