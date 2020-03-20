---
title: IMetaDataAssemblyImport::GetFileProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175976"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps 方法
使用指定的中繼資料簽名獲取檔的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdf`  
 [在]表示`mdFile`要為其獲取屬性的檔的中繼資料權杖。  
  
 `szName`  
 [出]檔的簡單名稱。  
  
 `cchName`  
 [在]大字元的大小`szName`。  
  
 `pchName`  
 [出]中實際返回的寬字元數`szName`。  
  
 `ppbHashValue`  
 [出]指向雜湊值的指標。 這是使用 SHA-1 演算法的檔雜湊。  
  
 `pcbHashValue`  
 [出]返回的雜湊值中的寬字元數。  
  
 `pdwFileFlags`  
 [出]指向描述應用於檔的中繼資料的標誌的指標。 標誌值是一個或多個[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)值的組合。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
