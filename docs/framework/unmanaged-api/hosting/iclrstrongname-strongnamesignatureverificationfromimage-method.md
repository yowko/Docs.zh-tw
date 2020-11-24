---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 134b32b6b281a08997849f4c23edfc1f357dadcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674394"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage 方法

驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
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

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRStrongName 介面](iclrstrongname-interface.md)
