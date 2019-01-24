---
title: IMetaDataImport2::GetMethodSpecProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69af794d5405894d24f0d7545613a0e85ca3ec6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574010"
---
# <a name="imetadataimport2getmethodspecprops-method"></a>IMetaDataImport2::GetMethodSpecProps 方法
取得指定 methodspec Neobsahuje 所參考之方法的中繼資料簽章語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a>參數  
 `mi`  
 [in]表示方法具現化 methodspec Neobsahuje 語彙基元。  
  
 `tkParent`  
 [out]表示方法定義的 MethodDef 或 MethodRef 語彙基元指標。  
  
 `ppvSigBlob`  
 [out]二進位中繼資料簽章方法的指標。  
  
 `pcbSigBlob`  
 [out]大小，以位元組為單位的`ppvSigBlob`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
