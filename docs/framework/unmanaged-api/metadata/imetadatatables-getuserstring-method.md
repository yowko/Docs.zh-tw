---
title: IMetaDataTables::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501140"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString 方法

取得在目前範圍的字串資料行中指定索引處的硬式編碼字串。

## <a name="syntax"></a>語法

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a>參數

`ixUserString`\
在將從中抓取硬式編碼字串的索引值。

`pcbData`\
脫銷大小的指標 `ppData` 。

`ppData`\
脫銷傳回之字串指標的指標。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Cor。h

連結**庫：** 做為 Mscoree.dll 中的資源使用

**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](imetadatatables-interface.md)
- [IMetaDataTables2 介面](imetadatatables2-interface.md)
