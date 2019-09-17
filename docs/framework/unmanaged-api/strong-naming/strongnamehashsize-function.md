---
title: StrongNameHashSize 函式
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799036"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize 函式
使用指定的雜湊演算法取得雜湊所需的緩衝區大小。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `ulHashAlg`  
 在用來計算緩衝區大小的雜湊演算法。  
  
 `pcbSize`  
 脫銷傳回的緩衝區大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 如果 `StrongNameHashSize` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameHashSize 方法](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
