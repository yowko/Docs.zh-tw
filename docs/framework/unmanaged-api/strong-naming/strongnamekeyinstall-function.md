---
title: StrongNameKeyInstall 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799001"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall 函式

將公開/私密金鑰組匯入到容器中。

這個函數已被取代。 請改用[ICLRStrongName：： StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)方法。

## <a name="syntax"></a>語法

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>參數

`wszKeyContainer`\
在金鑰容器的名稱。 `wszKeyContainer`必須是非空白字串。

`pbKeyBlob`\
在二進位金鑰組。

`cbKeyBlob`\
在的大小（以位元組為單位`pbKeyBlob`）。

## <a name="return-value"></a>傳回值

`true`成功完成時;否則為`false`。

## <a name="remarks"></a>備註

使用[StrongNameKeyDelete](strongnamekeydelete-function.md)函數來刪除金鑰容器。

如果 `StrongNameKeyInstall`函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Stackexchange.redis.strongname。h

**LIBRARY:** 包含為 Mscoree.dll 中的資源

**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [StrongNameKeyInstall 方法](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete 方法](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
