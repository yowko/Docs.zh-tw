---
title: StrongNameGetBlob 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095019"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob 函式
使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在要載入之可執行檔的有效路徑。  
  
 `pbBlob`  
 在要載入可執行檔的緩衝區。  
  
 `pcbBlob`  
 [in、out]`pbBlob`的要求大小上限（以位元組為單位）。 傳回時，`pbBlob`的實際大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 成功完成時 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 如果 `StrongNameGetBlob` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameGetBlob 方法](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage 方法](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
