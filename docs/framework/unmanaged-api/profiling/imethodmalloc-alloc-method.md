---
title: IMethodMalloc::Alloc 方法
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494198"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc 方法

嘗試為新的 Microsoft 中繼語言（MSIL）函數主體配置指定的記憶體數量。

## <a name="syntax"></a>語法

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>參數

`cb`\
在要配置給方法主體的位元組數目。

## <a name="remarks"></a>備註

 配置的記憶體會從大於與此配置器相關聯之模組基底位址的位址開始。 換句話說，每個配置器都會針對特定模組建立，並會嘗試在其基底位址的正位移上配置記憶體。 如果 `Alloc` 無法在大於模組基底位址的位址上配置要求的位元組數目，則會傳回 E_OUTOFMEMORY，不論實際的記憶體空間量為何。

 `Alloc`方法應該與[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法搭配使用。

## <a name="requirements"></a>規格需求
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** CorProf.idl、CorProf.h

 **程式庫：** CorGuids.lib

 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [IMethodMalloc 介面](imethodmalloc-interface.md)
