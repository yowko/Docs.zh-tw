---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ce29703a181106353695414e8b291b14c697fc56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444796"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9：： GetCodeInfo4 方法

假設機器碼的起始位址，會傳回儲存此程式碼的虛擬記憶體區塊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a>參數

`pNativeCodeStartAddress` \
在原生函式開頭的指標。

`cCodeInfos` \
[in] `codeInfos` 陣列的大小。

`pcCodeInfos` \
脫銷可用[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構總數的指標。

`codeInfos` \
[out] 呼叫者提供的緩衝區。 方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。

## <a name="remarks"></a>備註

`GetCodeInfo4` 方法類似于[GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)，不同之處在于它可以查閱方法的不同原生版本的程式碼資訊。

> [!NOTE]
> `GetCodeInfo4` 可以觸發垃圾收集。

範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。

`GetCodeInfo4` 傳回之後，您必須確認 `codeInfos` 緩衝區夠大，足以包含所有[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構。 若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。 如果 `cCodeInfos` 除以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構的大小小於 `pcCodeInfos`，請配置較大的 `codeInfos` 緩衝區、以新的、較大的大小更新 `cCodeInfos`，然後再次呼叫 `GetCodeInfo4`。

或者，您也可以先使用長度為零的 `GetCodeInfo4` 緩衝區來呼叫 `codeInfos`，以取得正確的緩衝區大小。 接著，您可以將 `codeInfos` 緩衝區大小設定為 `pcCodeInfos`中傳回的值，乘以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構的大小，然後再次呼叫 `GetCodeInfo4`。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo9 介面](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
