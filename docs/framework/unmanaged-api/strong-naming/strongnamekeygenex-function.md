---
title: StrongNameKeyGenEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: f28ee5767997240018d182b8303e4f65be81c702
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708539"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx 函式

使用指定的金鑰大小產生新的公開/私密金鑰組，以供強式名稱使用。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszKeyContainer`  
 在要求的金鑰容器名稱。 `wszKeyContainer` 必須是非空白字串，或 null 以產生暫存名稱。  
  
 `dwFlags`  
 在指定是否保留註冊的金鑰。 支援下列值：  
  
- 0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。  
  
- 0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。  
  
 `dwKeySize`  
 在要求的金鑰大小（以位為單位）。  
  
 `ppbKeyBlob`  
 擴展傳回的公開/私密金鑰組。  
  
 `pcbKeyBlob`  
 擴展的大小（以位元組為單位） `ppbKeyBlob` 。  
  
## <a name="return-value"></a>傳回值  

 `true` 成功完成時;否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 .NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位來簽署具有強式名稱的元件; 2.0 版新增了針對2048位金鑰支援的功能。  
  
 在抓取金鑰之後，您應該呼叫 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式來釋放配置的記憶體。  
  
 如果函式 `StrongNameKeyGenEx` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyGenEx 方法](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen 方法](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
