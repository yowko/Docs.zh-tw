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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49041031742332fbc275a9dbde91e640eb428c28
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785878"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>ICLRStrongName::StrongNameSignatureVerification 方法
取得值，指出是否提供之路徑上的組件資訊清單包含強式名稱簽章，根據指定的旗標加以確認。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]可攜式可執行檔 （.dll 或.exe） 檔來確認組件路徑。  
  
 `dwInFlags`  
 [in]若要修改的驗證行為的旗標。 支援下列值：  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。  
  
-   `SN_INFLAG_INSTALL` (0x00000002)-指定驗證資訊清單的第一次。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。  
  
 `pdwOutFlags`  
 [out]旗標，指出是否已驗證的強式名稱簽章。 支援下列值：  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [StrongNameSignatureVerificationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
