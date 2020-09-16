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
ms.openlocfilehash: ecaff179378eb417393c0a0d17d0a00d3b99e5a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541294"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9：： GetCodeInfo4 方法

在指定機器碼起始位址的情況下，傳回儲存此程式碼的虛擬記憶體區塊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>參數

- `pNativeCodeStartAddress`

  \[in] 原生函數開頭的指標。

- `cCodeInfos`

  \[in] 陣列的大小 `codeInfos` 。

- `pcCodeInfos`

  \[out] 可用 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構總數的指標。

- `codeInfos`

  \[out）提供者提供的緩衝區。 方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。

## <a name="remarks"></a>備註

`GetCodeInfo4`方法與[GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)類似，不同之處在于它可以查詢方法的不同原生版本的程式碼資訊。

> [!NOTE]
> `GetCodeInfo4` 可以觸發垃圾收集。

範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。

傳回之後 `GetCodeInfo4` ，您必須確認 `codeInfos` 緩衝區夠大，足以容納所有的 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構。 若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。 如果 `cCodeInfos` 除以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構的大小小於 `pcCodeInfos` ，請配置較大 `codeInfos` 的緩衝區， `cCodeInfos` 以新的、較大的大小進行更新，然後 `GetCodeInfo4` 再呼叫一次。

或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo4`，以取得正確的緩衝區大小。 然後，您可以將 `codeInfos` 緩衝區大小設定為傳回的值 `pcCodeInfos` （乘以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構的大小），然後再呼叫 `GetCodeInfo4` 一次。

## <a name="requirements"></a>需求

**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo9 介面](ICorProfilerInfo9-interface.md)
