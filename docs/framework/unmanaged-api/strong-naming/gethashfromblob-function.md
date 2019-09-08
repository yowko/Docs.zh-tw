---
title: GetHashFromBlob 函式
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799225"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob 函式

使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。

這個函數已被取代。 請改用[ICLRStrongName：： GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)方法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>參數

`pbBlob`\
在要雜湊的記憶體區塊位址的指標。

`cchBlob`\
在記憶體區塊的長度（以位元組為單位）。

`piHashAlg`\
[in、out]指定雜湊演算法的常數。 預設演算法使用零。

`pbHash`\
脫銷傳回的雜湊緩衝區。

`cchHash`\
在要求的大小`pbHash`上限。

`pchHash`\
脫銷傳回`pbHash`之的大小（以位元組為單位）。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Stackexchange.redis.strongname。h

**LIBRARY:** 包含為 Mscoree.dll 中的資源

**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [GetHashFromBlob 方法](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
