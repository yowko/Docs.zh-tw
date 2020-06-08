---
title: ICorProfilerInfo::SetILInstrumentedCodeMap 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: cac8e9570dab55af6b6e1fcf6f53b6a697727972
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502908"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap 方法

使用指定的 Microsoft 中繼語言（MSIL）對應專案，為指定的函式設定 Code Map。

> [!NOTE]
> 在 .NET Framework 版本2.0 中，在 `SetILInstrumentedCodeMap` `FunctionID` 代表特定應用程式域中泛型函式的上呼叫會影響應用程式域中該函式的所有實例。

## <a name="syntax"></a>語法

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>參數

`functionId`\
在要設定 Code Map 的函式識別碼。

`fStartJit`\
在布林值，指出對方法的呼叫是否為 `SetILInstrumentedCodeMap` 特定的第一個 `FunctionID` 。 `fStartJit` `true` 在第一次呼叫給定的時，將設為 `SetILInstrumentedCodeMap` `FunctionID` ，並在 `false` 之後設定為。

`cILMapEntries`\
在陣列中的元素數目 `cILMapEntries` 。

`rgILMapEntries`\
在COR_IL_MAP 結構的陣列，其中每一個都會指定一個 MSIL 位移。

## <a name="remarks"></a>備註

分析工具通常會在方法的原始程式碼中插入語句，以檢測該方法（例如，在到達指定的原始程式列時通知）。 `SetILInstrumentedCodeMap`可讓分析工具將原始 MSIL 指令對應至其新位置。 分析工具可以使用[ICorProfilerInfo：： GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md)方法來取得給定原生位移的原始 MSIL 位移。

偵錯工具會假設每個舊的位移都是指原始、未修改的 MSIL 程式碼內的 MSIL 位移，而且每個新的位移都會參考新檢測的程式碼內的 MSIL 位移。 對應應該以遞增順序排序。 若要讓逐步執行正常運作，請遵循下列指導方針：

- 請勿重新排列已檢測的 MSIL 程式碼。

- 請勿移除原始的 MSIL 程式碼。

- 在對應的程式資料庫（PDB）檔案中包含所有順序點的專案。 對應不會插補遺漏的專案。 因此，假設有下列對應：

  （0舊，0個新的）

  （5個或10個新的）

  （9個舊，20個新的）

  - 舊的位移為0、1、2、3或4，將會對應至新的位移0。

  - 舊的位移5、6、7或8會對應到新的位移10。

  - 舊的位移9或更高版本會對應到新的位移20。

  - 新的位移為0、1、2、3、4、5、6、7、8或9，將會對應到舊的位移0。

  - 10、11、12、13、14、15、16、17、18或19的新位移會對應到舊的位移5。

  - 新的位移20或以上會對應到舊的位移9。

在 .NET Framework 3.5 和之前的版本中，您可以 `rgILMapEntries` 呼叫[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)方法來配置陣列。 由於執行時間會取得此記憶體的擁有權，因此分析工具不應該嘗試釋放它。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
