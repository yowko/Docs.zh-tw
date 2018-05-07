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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5020c31f590f527856f966ede512e98c07496ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies 方法
判斷兩個組件是否只有其強式名稱簽章不同。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszAssembly1`  
 [in]第一個組件的路徑。  
  
 `wszAssembly2`  
 [in]第二個組件的路徑。  
  
 `pdwResult`  
 [out]下列值之一：  
  
-   `SN_CMP_DIFFERENT` (0)-指定的組件包含不同的資料。  
  
-   `SN_CMP_IDENTICAL` (1)-指定的組件完全相同，包括其簽章與總和檢查碼。  
  
-   `SN_CMP_SIGONLY` (2)-指定只要簽章與總和檢查碼不同組件。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>備註  
 組件的強式名稱簽章包含組件的文字名稱、 版本、 文化特性和公開金鑰語彙基元。  
  
## <a name="see-also"></a>另請參閱  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
