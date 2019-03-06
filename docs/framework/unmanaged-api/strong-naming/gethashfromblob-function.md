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
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352070"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob 函式

使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。

此函式已被取代。 使用[iclrstrongname:: Gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)方法改為。

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
[in]要雜湊的記憶體區塊的位址指標。

`cchBlob`\
[in]記憶體區塊的長度，以位元組為單位。

`piHashAlg`\
[in、 out]常數，指定的雜湊演算法。 使用零的預設演算法。

`pbHash`\
[out]傳回的雜湊緩衝區。

`cchHash`\
[in]要求的最大大小的`pbHash`。

`pchHash`\
[out]大小，以位元組為單位傳回`pbHash`。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** StrongName.h

**程式庫：** 包含做為 MsCorEE.dll 中的資源

**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [GetHashFromBlob 方法](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)