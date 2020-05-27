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
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007477"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps 方法
取得具有指定之中繼資料簽章之檔案的屬性。  
  
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
 在`mdFile`元資料標記，代表要取得其屬性的檔案。  
  
 `szName`  
 脫銷檔案名的簡單名稱。  
  
 `cchName`  
 在的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷中實際傳回的寬字元數 `szName` 。  
  
 `ppbHashValue`  
 脫銷雜湊值的指標。 這是檔案的雜湊，使用 SHA-1 演算法。  
  
 `pcbHashValue`  
 脫銷傳回的雜湊值中的寬字元數。  
  
 `pdwFileFlags`  
 脫銷旗標的指標，描述套用至檔案的中繼資料。 旗標值是一個或多個[CorFileFlags](corfileflags-enumeration.md)值的組合。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
