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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4eaf426bc9c933de1d4b774928f2b0a54dfb472
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636939"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString 方法

取得在目前範圍中的字串資料行中的指定索引處的硬式編碼的字串。

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
[in]硬式編碼的字串將擷取的索引值。

`pcbData`\
[out]大小的指標`ppData`。

`ppData`\
[out]傳回的字串指標的指標。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** Cor.h

**LIBRARY:** 做為 MsCorEE.dll 中的資源

**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [IMetaDataTables 介面](imetadatatables-interface.md)
- [IMetaDataTables2 介面](imetadatatables2-interface.md)
