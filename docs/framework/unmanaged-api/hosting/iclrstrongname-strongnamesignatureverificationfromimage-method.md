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
ms.openlocfilehash: adb3b4e33edafe6d25c8259e316a9b62e339f896
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092675"
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
 在對應之組件資訊清單的相對虛擬位址。  
  
 `dwLength`  
 在對應影像的大小（以位元組為單位）。  
  
 `dwInFlags`  
 在會影響驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER` （0x00000001）-即使需要覆寫登錄設定，也會強制執行驗證。  
  
- `SN_INFLAG_INSTALL` （0x00000002）-指定這是在此影像上執行的第一次驗證。  
  
- `SN_INFLAG_ADMIN_ACCESS` （0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。  
  
- `SN_INFLAG_USER_ACCESS` （0x00000008）-指定只有目前使用者可以存取元件。  
  
- `SN_INFLAG_ALL_ACCESS` （0x00000010）-指定快取不會提供存取限制的保證。  
  
- `SN_INFLAG_RUNTIME` （0x80000000）-保留供內部偵錯工具之用。  
  
 `pdwOutFlags`  
 脫銷其他輸出資訊的旗標。 支援下列值：  
  
- `SN_OUTFLAG_WAS_VERIFIED` （0x00000001）-此值設定為 `false`，指定驗證是因為登錄設定而成功。  
  
## <a name="return-value"></a>傳回值  
 如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
