---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: cf599e5ded73b09d54c98dcd99f51b30c6a4ba82
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661193"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a>ICorProfilerInfo10:: ResumeRuntime 方法

繼續執行時間, 而不執行 GC。

## <a name="syntax"></a>語法

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a>需求

**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
