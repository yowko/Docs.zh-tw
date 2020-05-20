---
title: IXCLRDataModule：： Request 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420808"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule：： Request 方法

要求填入模組資料所提供的緩衝區。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>參數

`reqCode`\
在要傳送的要求類型。

`inBufferSize`\
[in] 要傳入之輸入緩衝區的大小。

`inBuffer`\
[in，size_is （inBufferSize）]要在要求中傳送之原始資料的緩衝區指標。

`outBufferSize`\
在輸出緩衝區的大小。

`outBuffer`\
[out，size_is （outBufferSize）]用來儲存要求回應的緩衝區指標。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `IXCLRDataModule` ，而且會對應至虛擬方法資料表的37th 位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。
**標頭：** 無**媒體櫃：** 無 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [IXCLRDataModule 介面](ixclrdatamodule-interface.md)
