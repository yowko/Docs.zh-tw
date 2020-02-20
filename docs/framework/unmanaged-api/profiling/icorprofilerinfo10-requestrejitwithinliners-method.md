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
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452171"
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

## <a name="parameters"></a>參數

- `dwRejitFlags`

  \[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)的位元遮罩。

- `cFunctions`

  \[in] 要重新編譯的函式數目。

- `moduleIds`

  中的 \[] 指定（`module`，`methodDef`）配對的 `moduleId` 部分，識別要重新編譯的函式。

- `methodIds`

  中的 \[] 指定（`module`，`methodDef`）配對的 `methodId` 部分，識別要重新編譯的函式。

## <a name="remarks"></a>備註

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md)不會對內嵌的方法進行任何追蹤。 分析工具預期會封鎖內嵌或追蹤內嵌，並為所有 inliners 呼叫 `RequestReJIT`，以確保內嵌方法的每個實例都已 ReJITted。 這會造成 ReJIT on attach 的問題，因為分析工具不存在來監視內嵌。 您可以呼叫這個方法，以確保一組完整的 inliners 也會 ReJITted。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](icorprofilerinfo10-interface.md)
