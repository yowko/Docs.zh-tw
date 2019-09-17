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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22339b7d48e89f99d1500cfdda53f00f1234b80
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799074"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 函式
驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)方法。  
  
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
 在對應之組件資訊清單的相對虛擬位址。  
  
 `dwLength`  
 在對應影像的大小（以位元組為單位）。  
  
 `dwInFlags`  
 在會影響驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER`（0x00000001）-強制進行驗證，即使需要覆寫登錄設定也一樣。  
  
- `SN_INFLAG_INSTALL`（0x00000002）-指定這是在此影像上執行的第一次驗證。  
  
- `SN_INFLAG_ADMIN_ACCESS`（0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。  
  
- `SN_INFLAG_USER_ACCESS`（0x00000008）-指定只有目前的使用者可以存取此元件。  
  
- `SN_INFLAG_ALL_ACCESS`（0x00000010）-指定快取不會提供存取限制的保證。  
  
- `SN_INFLAG_RUNTIME`（0x80000000）-保留供內部偵錯工具之用。  
  
 `pdwOutFlags`  
 脫銷其他輸出資訊的旗標。 支援下列值：  
  
- `SN_OUTFLAG_WAS_VERIFIED`（0x00000001）-此值設定`false`為，以指定驗證因為登錄設定而成功。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 如果函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。`StrongNameSignatureVerificationFromImage`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerificationFromImage 方法](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
