---
title: IMetaDataImport::GetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 3c7c3525f2f8753241c9a206e4cf5e552bf06efe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503618"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps 方法
取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mb`  
 在MethodDef token，表示要傳回中繼資料的方法。  
  
 `pClass`  
 脫銷TypeDef token 的指標，表示可執行方法的類型。  
  
 `szMethod`  
 脫銷具有方法名稱之緩衝區的指標。  
  
 `cchMethod`  
 在要求的大小 `szMethod` 。  
  
 `pchMethod`  
 脫銷大小的指標，以寬字元為單位 `szMethod` ，或在截斷的情況下，為方法名稱中的寬字元實際數目。  
  
 `pdwAttr`  
 脫銷與方法相關聯之任何旗標的指標。  
  
 `ppvSigBlob`  
 脫銷方法之二進位中繼資料簽章的指標。  
  
 `pcbSigBlob`  
 脫銷大小的指標，以位元組為單位 `ppvSigBlob` 。  
  
 `pulCodeRVA`  
 脫銷方法之相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 脫銷方法之任何執行旗標的指標。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
