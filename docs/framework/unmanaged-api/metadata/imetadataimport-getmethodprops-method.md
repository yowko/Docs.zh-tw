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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps 方法
取得與指定 MethodDef 語彙基元所參考方法相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `mb`  
 [in]表示要傳回的中繼資料的方法 MethodDef 語彙基元。  
  
 `pClass`  
 [out]代表實作方法的型別 TypeDef 語彙基元的指標。  
  
 `szMethod`  
 [out]方法的名稱緩衝區的指標。  
  
 `cchMethod`  
 [in]要求的大小`szMethod`。  
  
 `pchMethod`  
 [out]中的寬字元大小的指標`szMethod`，如果發生截斷情形，實際的方法名稱中的寬字元數目。  
  
 `pdwAttr`  
 [out]與方法相關聯的任何旗標指標。  
  
 `ppvSigBlob`  
 [out]方法的二進位中繼資料簽章指標。  
  
 `pcbSigBlob`  
 [out]以位元組為單位的大小的指標`ppvSigBlob`。  
  
 `pulCodeRVA`  
 [out]方法的相對虛擬位址指標。  
  
 `pdwImplFlags`  
 [out]任何方法的實作旗標指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
