---
title: ICLRStrongName::StrongNameTokenFromAssembly 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: e71fcf80b51edc318bbc7d81bb277c614184ee55
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762509"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a>ICLRStrongName::StrongNameTokenFromAssembly 方法
從指定的組件檔案建立強式名稱權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在元件的可移植執行檔（PE）路徑。  
  
 `ppbStrongNameToken`  
 脫銷傳回的強式名稱 token。  
  
 `pcbStrongNameToken`  
 脫銷強式名稱 token 的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="remarks"></a>備註  
 強式名稱 token 是公用金鑰的縮寫格式。 Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。 Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。  
  
 建立權杖之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromAssemblyEx 方法](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
