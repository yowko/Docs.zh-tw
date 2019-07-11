---
title: StrongNameTokenFromAssembly 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 484dacd4d9803139edf3fd5bad22c164d50de3dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757248"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 函式
從指定的組件檔案建立強式名稱權杖。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]組件的可攜式執行檔 (PE) 檔案的路徑。  
  
 `ppbStrongNameToken`  
 [out]傳回的強式名稱語彙基元。  
  
 `pcbStrongNameToken`  
 [out]大小，以位元組為單位的強式名稱語彙基元。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果成功地完成;否則， `false`。  
  
## <a name="remarks"></a>備註  
 強式名稱語彙基元是公開金鑰的縮短格式。 64 位元雜湊建立用來簽署組件的公開金鑰權杖。 此權杖是組件的強式名稱的一部分，而且可以讀取組件中繼資料。  
  
 建立權杖之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式來釋放配置的記憶體。  
  
 如果`StrongNameTokenFromAssembly`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **LIBRARY:** 包含做為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromAssembly 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
