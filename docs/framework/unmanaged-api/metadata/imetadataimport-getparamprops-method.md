---
title: IMetaDataImport::GetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449321"
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps 方法
取得指定 ParamDef 語彙基元所參考參數的中繼資料值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `tk`  
 [in]ParamDef 語彙基元，代表要傳回的中繼資料的參數。  
  
 `pmd`  
 [out]代表方法的 MethodDef 語彙基元的指標會接受參數。  
  
 `pulSequence`  
 [out]方法引數清單中的參數序數位置。  
  
 `szName`  
 [out]要保存的參數名稱的緩衝區。  
  
 `cchName`  
 [in]要求的大小，以寬字元`szName`。  
  
 `pchName`  
 [out]傳回的大小的寬字元`szName`。  
  
 `pdwAttr`  
 [out]任何參數相關聯的屬性旗標指標。  
  
 `pdwCPlusTypeFlag`  
 [out]指向的旗標，指定參數是否為<xref:System.ValueType>。  
  
 `ppValue`  
 [out]參數所傳回的常數字串指標。  
  
 `pcchValue`  
 [out]大小`ppValue`寬字元，或如果`ppValue`不會保存一個字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
