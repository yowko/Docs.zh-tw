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
ms.openlocfilehash: 0087636c68d0748ad2b143de9b132278ab9d43f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762054"
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
  
- `SN_CMP_DIFFERENT`（0）-指定元件包含不同的資料。  
  
- `SN_CMP_IDENTICAL`（1）-指定元件完全相同，包括其簽章和總和檢查碼。  
  
- `SN_CMP_SIGONLY`（2）-指定元件只有簽章和總和檢查碼不同。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>備註  
 元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。  
  
## <a name="see-also"></a>另請參閱

- [ICLRStrongName 介面](iclrstrongname-interface.md)
