---
title: IMetaDataEmit::TranslateSigWithScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003948"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope 方法
將元件匯入到目前的範圍，並為合併的範圍取得新的中繼資料簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a>參數  
 `pAssemImport`  
 在匯入元件的介面（定義簽章的位置）。  
  
 `pbHashValue`  
 在元件的雜湊 blob。  
  
 `cbHashValue`  
 在中的位元組計數 `pbHashValue` 。  
  
 `import`  
 在匯入中繼資料範圍的介面。  
  
 `pbSigBlob`  
 在要匯入的簽章。  
  
 `cbSigBlob`  
 在的大小（以位元組為單位） `pbSigBlob` 。  
  
 `pAssemEmit`  
 在匯出元件的介面。  
  
 `emit`  
 在用於匯出中繼資料範圍的介面。  
  
 `pvTranslatedSig`  
 脫銷保存已轉譯之簽章 blob 的緩衝區。  
  
 `cbTranslatedSigMax`  
 在的容量（以位元組為單位） `pvTranslatedSig` 。  
  
 `pcbTranslatedSig`  
 脫銷翻譯簽章中的實際位元組數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
