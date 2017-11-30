---
title: "StrongNameSignatureVerificationFromImage 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab890451c44b19be6472ae6c7da060ae71612bc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 函式
請確認已對應到記憶體的組件適用於相關聯的公開金鑰。  
  
 此函式已被取代。 使用[ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbBase`  
 [in]對應的組件資訊清單的相對虛擬位址。  
  
 `dwLength`  
 [in]以位元組為單位的對應影像大小。  
  
 `dwInFlags`  
 [in]影響驗證行為的旗標。 支援下列值：  
  
-   `SN_INFLAG_FORCE_VER`(0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。  
  
-   `SN_INFLAG_INSTALL`(0x00000002)-指定此映像上執行的第一個驗證。  
  
-   `SN_INFLAG_ADMIN_ACCESS`(0x00000004)-指定快取可讓擁有系統管理權限的使用者存取。  
  
-   `SN_INFLAG_USER_ACCESS`(0x00000008)-指定的組件都是只能由目前的使用者存取。  
  
-   `SN_INFLAG_ALL_ACCESS`(0x00000010)-指定快取會提供任何保證的存取限制。  
  
-   `SN_INFLAG_RUNTIME`(0x80000000)-保留供內部偵錯。  
  
 `pdwOutFlags`  
 [out]其他輸出資訊的旗標。 支援下列值：  
  
-   `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-此值設為`false`來指定驗證成功登錄設定所造成。  
  
## <a name="return-value"></a>傳回值  
 `true`如果成功地完成。否則， `false`。  
  
## <a name="remarks"></a>備註  
 如果`StrongNameSignatureVerificationFromImage`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **程式庫：**包含做為 mscoree.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [StrongNameSignatureVerificationFromImage 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
