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
ms.openlocfilehash: 0eb4e9d713581cf32cec18bb02a6bd13542e517a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733176"
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
 在MethodDef token，表示傳回中繼資料的方法。  
  
 `pClass`  
 擴展TypeDef token 的指標，表示執行方法的型別。  
  
 `szMethod`  
 擴展具有方法名稱之緩衝區的指標。  
  
 `cchMethod`  
 在要求的大小 `szMethod` 。  
  
 `pchMethod`  
 擴展以寬字元為單位的大小指標 `szMethod` ，或在截斷的情況下，在方法名稱中的寬字元實際數目。  
  
 `pdwAttr`  
 擴展與方法相關聯之任何旗標的指標。  
  
 `ppvSigBlob`  
 擴展方法的二進位中繼資料簽章指標。  
  
 `pcbSigBlob`  
 擴展大小的指標，以位元組為單位 `ppvSigBlob` 。  
  
 `pulCodeRVA`  
 擴展方法的相對虛擬位址指標。  
  
 `pdwImplFlags`  
 擴展方法之任何執行旗標的指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
