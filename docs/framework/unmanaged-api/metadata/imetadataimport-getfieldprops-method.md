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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177239"
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
 [在]表示要為其獲取關聯的中繼資料的欄位的 FieldDef 權杖。  
  
 `pClass`  
 [出]指向 TypeDef 權杖的指標，表示欄位所屬的類的類型。  
  
 `szField`  
 [出]欄位的名稱。  
  
 `cchField`  
 [在]*szField*緩衝區的大小以寬字元表示。  
  
 `pchField`  
 [出]返回的緩衝區的實際大小。  
  
 `pdwAttr`  
 [出]與欄位的中繼資料關聯的標誌。  
  
 `ppvSigBlob`  
 [在]指向描述欄位的二進位中繼資料值的指標。  
  
 `pcbSigBlob`  
 [出]的大小（以位元組為單位）。 `ppvSigBlob`  
  
 `pdwCPlusTypeFlag`  
 [出]指定欄位的數值型別的標誌。  
  
 `ppValue`  
 [出]欄位的常量值。  
  
 `pcchValue`  
 [出]如果不存在字串，則大小`ppValue`以 的 字元表示或零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
