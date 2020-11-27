---
title: IXCLRDataProcess：： GetRuntimeNameByAddress 方法
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270481"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>IXCLRDataProcess：： GetRuntimeNameByAddress 方法

取得指定位址的名稱。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a>參數

`address`\
在 `CLRDATA_ADDRESS` 表示程式碼位址的值。

`flags`\
在設定為 ' 0 '。

`bufLen`\
在緩衝區的長度。

`namLen`\
擴展傳回的字元數指標。

`namBuf`\
[out，size_is (`bufLen`) ] 儲存執行時間名稱之長度的輸入緩衝區 `bufLen` 。

`displacement`\
擴展 `CLRDATA_ADDRESS` 傳回之符號的程式碼位移指標。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的第16個位置。

> [!NOTE]
> 如果緩衝區不夠大，無法用於名稱，這個方法會傳回 `S_FALSE` 並設定 `nameLen` 為所需的緩衝區長度。

## <a name="requirements"></a>規格需求

**平臺：** 查看 [系統需求](../../get-started/system-requirements.md)\
**標頭：** 以上
連結 **庫：** 以上
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [IXCLRDataProcess 介面](ixclrdataprocess-interface.md)
