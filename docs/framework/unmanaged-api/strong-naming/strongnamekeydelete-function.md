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
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040764"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete 函式

刪除指定的金鑰容器。

此函式已被取代。 使用[iclrstrongname:: Strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)方法改為。

## <a name="syntax"></a>語法

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>參數

`wszKeyContainer`\
[in]若要刪除的金鑰容器名稱。

## <a name="return-value"></a>傳回值

`true` 如果成功地完成;否則， `false`。

## <a name="remarks"></a>備註

使用[StrongNameKeyInstall](strongnamekeyinstall-function.md)函式來匯入到容器的公開/私密金鑰組。

如果`StrongNameKeyDelete`函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** StrongName.h

**LIBRARY:** 包含做為 MsCorEE.dll 中的資源

**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [StrongNameKeyDelete 方法](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall 方法](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)