---
title: IMetaDataAssemblyImport::GetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177651"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps 方法
使用指定的中繼資料簽名獲取清單資源的屬性集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdmr`  
 [在]表示`mdManifestResource`要為其獲取屬性的資源的權杖。  
  
 `szName`  
 [出]資源的名稱。  
  
 `cchName`  
 [在]大字元的大小`szName`。  
  
 `pchName`  
 [出]指向 中實際返回的寬字元數的指標`szName`。  
  
 `ptkImplementation`  
 [出]指向分別表示包含`mdFile`資源的檔或`mdAssemblyRef`程式集的權杖或權杖的指標。  
  
 `pdwOffset`  
 [出]指向指定偏移到檔中資源開頭的值的指標。  
  
 `pdwResourceFlags`  
 [出]指向用於描述應用於資源的中繼資料的標誌的指標。 標誌值是一個或多個[CorManifest 資源標誌](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)值的組合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
