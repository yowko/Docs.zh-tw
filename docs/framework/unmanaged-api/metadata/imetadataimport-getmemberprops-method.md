---
title: IMetaDataImport::GetMemberProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcf32c4b27324ccc54eabbb248e8c9906cf693b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782353"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps 方法
取得儲存在指定的成員定義，包括名稱、 二進位簽章和相對虛擬位址的中繼資料中的資訊<xref:System.Type>指定之中繼資料語彙基元所參考的成員。 這是一個簡單的 helper 方法： 如果*mb*就的 MethodDef **GetMethodProps**呼叫; 如果*mb*就的 fielddef 語彙**GetFieldProps**會呼叫。 請參閱這些其他方法，如需詳細資訊。 
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `mb`  
 [in]參考的成員，以取得相關聯中繼資料語彙基元。  
  
 `pClass`  
 [out]表示的類別成員的中繼資料語彙基元指標。  
  
 `szMember`  
 [out]成員的名稱。  
  
 `cchMember`  
 [in]寬字元大小`szMember`緩衝區。  
  
 `pchMember`  
 [out]寬字元，傳回的檔案名稱的大小。  
  
 `pdwAttr`  
 [out]任何旗標套用至成員的值。  
  
 `ppvSigBlob`  
 [out]二進位中繼資料簽章的成員指標。  
  
 `pcbSigBlob`  
 [out]以位元組為單位的大小`ppvSigBlob`。  
  
 `pulCodeRVA`  
 [out]成員的相對虛擬位址指標。  
  
 `pdwImplFlags`  
 [out]成員相關聯任何方法實作旗標。  
  
 `pdwCPlusTypeFlag`  
 [out]標示旗標<xref:System.ValueType>。 它是其中一個`ELEMENT_TYPE_*`值。
  
 `ppValue`  
 [out]常數字串值，這個成員所傳回。  
  
 `pcchValue`  
 [out]以字元為單位的大小`ppValue`，或零，如果`ppValue`不會保留為字串。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
