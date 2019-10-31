---
title: ICLRStrongName::StrongNameCompareAssemblies 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135153"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies 方法
判斷兩個組件是否只有強制名稱簽章不同。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszAssembly1`  
 在第一個元件的路徑。  
  
 `wszAssembly2`  
 在第二個元件的路徑。  
  
 `pdwResult`  
 脫銷下列其中一個值：  
  
- `SN_CMP_DIFFERENT` （0）-指定元件包含不同的資料。  
  
- `SN_CMP_IDENTICAL` （1）-指定元件完全相同，包括其簽章和總和檢查碼。  
  
- `SN_CMP_SIGONLY` （2）-指定元件只有簽章和總和檢查碼不同。  
  
## <a name="return-value"></a>傳回值  
 如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>備註  
 元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。  
  
## <a name="see-also"></a>請參閱

- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
