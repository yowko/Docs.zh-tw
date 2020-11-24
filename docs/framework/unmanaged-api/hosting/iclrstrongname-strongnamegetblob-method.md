---
title: ICLRStrongName::StrongNameGetBlob 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 824dcf89bacec27ced7cc431a9646d00fb879430
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674667"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a>ICLRStrongName::StrongNameGetBlob 方法

使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameGetBlob (  
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

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetBlobFromImage 方法](iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
