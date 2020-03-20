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
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177223"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps 方法
獲取存儲在指定成員定義的中繼資料中的資訊，包括指定中繼資料權杖引用<xref:System.Type>的成員的名稱、二進位簽名和相對虛擬位址。 這是一個簡單的説明方法：如果*mb*是一個方法Def，則調用**GetMethodProps;** 如果*mb*是 FieldDef，則調用**GetFieldProps。** 有關詳細資訊，請參閱這些其他方法。
  
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
 [在]引用成員獲取關聯的中繼資料的權杖。  
  
 `pClass`  
 [出]指向表示成員類的中繼資料權杖的指標。  
  
 `szMember`  
 [出]成員的名稱。  
  
 `cchMember`  
 [在]`szMember`緩衝區的大小以寬字元表示。  
  
 `pchMember`  
 [出]返回名稱的寬字元大小。  
  
 `pdwAttr`  
 [出]應用於成員的任何標誌值。  
  
 `ppvSigBlob`  
 [出]指向成員的二進位中繼資料簽名的指標。  
  
 `pcbSigBlob`  
 [出]的大小（以位元組為單位）。 `ppvSigBlob`  
  
 `pulCodeRVA`  
 [出]指向成員的相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 [出]與成員關聯的任何方法實現標誌。  
  
 `pdwCPlusTypeFlag`  
 [出]標記 的標誌<xref:System.ValueType>。 它是`ELEMENT_TYPE_*`值之一。
  
 `ppValue`  
 [出]此成員返回的常量字串值。  
  
 `pcchValue`  
 [出]如果`ppValue`不保存字串，`ppValue`則以 字元或零表示的大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
