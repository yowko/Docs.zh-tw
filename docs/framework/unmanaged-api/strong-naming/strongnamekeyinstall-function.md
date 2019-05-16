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
ms.openlocfilehash: 7121ace6777e7cf947fcc6ff30b1ea314851feff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636709"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall 函式

將公開/私密金鑰組匯入到容器中。

此函式已被取代。 使用[iclrstrongname:: Strongnamekeyinstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)方法改為。

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
[in]金鑰容器的名稱。 `wszKeyContainer` 必須是非空白字串。

`pbKeyBlob`\
[in]二進位金鑰組。

`cbKeyBlob`\
[in]大小，以位元組為單位的`pbKeyBlob`。

## <a name="return-value"></a>傳回值

`true` 如果成功地完成;否則， `false`。

## <a name="remarks"></a>備註

使用[StrongNameKeyDelete](strongnamekeydelete-function.md)函式來刪除金鑰容器。

如果`StrongNameKeyInstall`函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** StrongName.h

**LIBRARY:** 包含做為 MsCorEE.dll 中的資源

**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [StrongNameKeyInstall 方法](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete 方法](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
