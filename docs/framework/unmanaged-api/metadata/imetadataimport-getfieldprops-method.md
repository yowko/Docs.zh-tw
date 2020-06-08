---
title: IMetaDataImport::GetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491239"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps 方法
取得與指定 FieldDef 語彙基元所參考欄位相關聯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `mb`  
 在FieldDef token，表示要取得相關聯中繼資料的欄位。  
  
 `pClass`  
 脫銷TypeDef token 的指標，代表欄位所屬類別的型別。  
  
 `szField`  
 脫銷欄位的名稱。  
  
 `cchField`  
 在*SzField*緩衝區的大小（以寬字元為單位）。  
  
 `pchField`  
 脫銷所傳回緩衝區的實際大小。  
  
 `pdwAttr`  
 脫銷與欄位的中繼資料相關聯的旗標。  
  
 `ppvSigBlob`  
 在描述欄位之二進位中繼資料值的指標。  
  
 `pcbSigBlob`  
 脫銷的大小（以位元組為單位） `ppvSigBlob` 。  
  
 `pdwCPlusTypeFlag`  
 脫銷指定欄位之數值型別的旗標。  
  
 `ppValue`  
 脫銷欄位的常數值。  
  
 `pcchValue`  
 脫銷的大小（以字元為單位 `ppValue` ），如果不存在任何字串，則為零。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
