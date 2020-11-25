---
title: IMetaDataImport::GetTypeDefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 9dd973fe3e0802c49c220db51a21c223730e5aec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729158"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps 方法

傳回指定之 TypeDef token 所表示的中繼資料資訊 <xref:System.Type> 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>參數  

 `td`  
 在表示傳回中繼資料之類型的 TypeDef 標記。  
  
 `szTypeDef`  
 擴展包含型別名稱的緩衝區。  
  
 `cchTypeDef`  
 在的大小（以寬字元為單位） `szTypeDef` 。  
  
 `pchTypeDef`  
 擴展傳回的寬字元數 `szTypeDef` 。  
  
 `pdwTypeDefFlags`  
 擴展任何修改類型定義之旗標的指標。 這個值是 [CorTypeAttr](cortypeattr-enumeration.md) 列舉的位元遮罩。  
  
 `ptkExtends`  
 擴展TypeDef 或 TypeRef 元資料標記，代表所要求之型別的基底型別。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
