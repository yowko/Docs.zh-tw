---
title: StrongNameGetBlobFromImage 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799094"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage 函式
取得位於所指定記憶體位置之組件影像的二進位表示法。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbBase`  
 在對應的組件資訊清單的記憶體位址。  
  
 `dwLength`  
 在影像的大小（以位元組為單位） `pbBase`。  
  
 `pbBlob`  
 在包含影像之二進位表示的緩衝區。  
  
 `pcbBlob`  
 [in、out]要求的大小上限（以位元組為單位`pbBlob`）。 傳回時，為的實際大小（以位元組為`pbBlob`單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 如果函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。`StrongNameGetBlobFromImage`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetBlobFromImage 方法](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob 方法](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
