---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 74300a12d000565a63cd7ea862c759d47b87bbe1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665702"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a>ICorProfilerInfo10:: SuspendRuntime 方法

暫停執行時間, 而不執行 GC。

## <a name="syntax"></a>語法

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a>需求

**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
