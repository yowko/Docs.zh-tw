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
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732277"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob 函式

使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) 方法。  
  
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
 在要在其中載入可執行檔的緩衝區。  
  
 `pcbBlob`  
 [in，out]要求的大小上限（以位元組為單位） `pbBlob` 。 傳回時，的實際大小（以位元組為單位） `pbBlob` 。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 如果函式 `StrongNameGetBlob` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetBlob 方法](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage 方法](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
