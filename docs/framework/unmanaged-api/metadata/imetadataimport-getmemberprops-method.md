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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437513"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps 方法
針對指定的元資料標記所參考的 <xref:System.Type> 成員，取得儲存在中繼資料中的特定成員定義的資訊，包括名稱、二進位簽章和相對虛擬位址。 這是簡單的 helper 方法：如果*mb*是 MethodDef，則會呼叫**GetMethodProps** ;如果*mb*是 FieldDef，則會呼叫**GetFieldProps** 。 如需詳細資訊，請參閱這些其他方法。 
  
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
 在參考要取得相關聯中繼資料之成員的 token。  
  
 `pClass`  
 脫銷元資料標記的指標，表示成員的類別。  
  
 `szMember`  
 脫銷成員的名稱。  
  
 `cchMember`  
 在`szMember` 緩衝區的大小（以寬字元為單位）。  
  
 `pchMember`  
 脫銷傳回名稱的大小（以寬字元為單位）。  
  
 `pdwAttr`  
 脫銷套用至成員的任何旗標值。  
  
 `ppvSigBlob`  
 脫銷成員的二進位中繼資料簽章的指標。  
  
 `pcbSigBlob`  
 脫銷`ppvSigBlob`的大小（以位元組為單位）。  
  
 `pulCodeRVA`  
 脫銷成員之相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 脫銷與成員相關聯的任何方法執行旗標。  
  
 `pdwCPlusTypeFlag`  
 脫銷標記 <xref:System.ValueType>的旗標。 這是其中一個 `ELEMENT_TYPE_*` 值。
  
 `ppValue`  
 脫銷這個成員傳回的常數位串值。  
  
 `pcchValue`  
 脫銷`ppValue`的大小（以字元為單位），如果 `ppValue` 不包含字串，則為零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
