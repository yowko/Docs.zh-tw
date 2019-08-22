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
ms.openlocfilehash: 00bfc9fc21ed39226fd21c4096305c254d73ee11
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665718"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners 方法

ReJITs 要求的方法, 以及所要求之方法的任何 inliners。

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
[in] 指定 (`module`, `methodDef`) 組的 `moduleId` 部分，這個部分可識別所要重新編譯的函式。

`methodIds` \
[in] 指定 (`module`, `methodDef`) 組的 `methodId` 部分，這個部分可識別所要重新編譯的函式。

## <a name="remarks"></a>備註

[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)不會對內嵌的方法進行任何追蹤。 分析工具預期會封鎖內嵌或追蹤內嵌, 並針對所有`RequestReJIT` inliners 呼叫, 以確保內嵌方法的每個實例都已 ReJITted。 這會造成 ReJIT on attach 的問題, 因為分析工具不存在來監視內嵌。 您可以呼叫這個方法, 以確保一組完整的 inliners 也會 ReJITted。

## <a name="requirements"></a>需求

**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
