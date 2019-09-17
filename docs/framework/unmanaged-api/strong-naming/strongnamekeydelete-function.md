---
title: StrongNameKeyDelete 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799027"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete 函式

刪除指定的金鑰容器。

這個函數已被取代。 請改用[ICLRStrongName：： StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)方法。

## <a name="syntax"></a>語法

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>參數

`wszKeyContainer`\
在要刪除的金鑰容器名稱。

## <a name="return-value"></a>傳回值

`true`成功完成時;否則為`false`。

## <a name="remarks"></a>備註

使用[StrongNameKeyInstall](strongnamekeyinstall-function.md)函數，將公開/私密金鑰組匯入容器。

如果 `StrongNameKeyDelete` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Stackexchange.redis.strongname。h

**LIBRARY:** 包含為 Mscoree.dll 中的資源

**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [StrongNameKeyDelete 方法](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall 方法](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
