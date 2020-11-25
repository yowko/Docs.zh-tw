---
title: StrongNameSignatureVerificationFromImage 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: b90cc6fe99cf592f1b3fd117888462a957e4ce35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708422"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 函式

驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbBase`  
 在對應的組件資訊清單的相對虛擬位址。  
  
 `dwLength`  
 在對應影像的大小（以位元組為單位）。  
  
 `dwInFlags`  
 在影響驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) -即使必須覆寫登錄設定，仍會強制執行驗證。  
  
- `SN_INFLAG_INSTALL` (0x00000002) -指定這是在此映射上執行的第一次驗證。  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) -指定快取只允許具有系統管理許可權的使用者存取。  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) -指定只有目前使用者才能存取元件。  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) -指定快取不會提供存取限制的保證。  
  
- `SN_INFLAG_RUNTIME` (0x80000000) -保留供內部偵錯工具之用。  
  
 `pdwOutFlags`  
 擴展額外輸出資訊的旗標。 以下是支援的值：  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) -此值設定為， `false` 以指定驗證成功，因為登錄設定。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 如果函式 `StrongNameSignatureVerificationFromImage` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerificationFromImage 方法](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
