---
title: ICLRStrongName::StrongNameSignatureVerification 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 2d53eebcc272ab87a2af5b3c081ca37dde5c74b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674463"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>ICLRStrongName::StrongNameSignatureVerification 方法

取得值，這個值會指出所提供路徑的組件資訊清單是否包含強式名稱簽章，並根據指定的旗標進行驗證。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszFilePath`  
 在可攜式可執行檔的路徑 ( .dll 或 .exe) 檔，以供元件進行驗證。  
  
 `dwInFlags`  
 在用以修改驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) -即使必須覆寫登錄設定，仍會強制執行驗證。  
  
- `SN_INFLAG_INSTALL` (0x00000002) -指定這是資訊清單的第一次驗證。  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) -指定快取只允許具有系統管理許可權的使用者存取。  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) -指定只有目前使用者才能存取元件。  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) -指定快取不會提供存取限制的保證。  
  
- `SN_INFLAG_RUNTIME` (0x80000000) -保留供內部偵錯工具之用。  
  
 `pdwOutFlags`  
 擴展旗標，指出是否已驗證強式名稱簽章。 以下是支援的值：  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) -此值設定為， `false` 以指定驗證成功，因為登錄設定。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerificationEx 方法](iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
