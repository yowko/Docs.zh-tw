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
ms.openlocfilehash: f01d65a339c77e6af3e768c620f17ef0190c1e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733213"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps 方法

針對指定的元資料標記所參考的成員，取得儲存在中繼資料中的指定成員定義，包括名稱、二進位簽章和相對虛擬位址 <xref:System.Type> 。 這是簡單的 helper 方法：如果有 *mb* 是 MethodDef，則會呼叫 **GetMethodProps** ;如果 *mb* 是 FieldDef，則會呼叫 **GetFieldProps** 。 如需詳細資訊，請參閱這些其他方法。
  
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
 在參考成員以取得相關聯中繼資料的權杖。  
  
 `pClass`  
 擴展元資料標記的指標，表示成員的類別。  
  
 `szMember`  
 擴展成員的名稱。  
  
 `cchMember`  
 在緩衝區的大小（以寬字元為單位） `szMember` 。  
  
 `pchMember`  
 擴展傳回名稱的大小（以寬字元為單位）。  
  
 `pdwAttr`  
 擴展套用至成員的任何旗標值。  
  
 `ppvSigBlob`  
 擴展成員的二進位中繼資料簽章指標。  
  
 `pcbSigBlob`  
 擴展的大小（以位元組為單位） `ppvSigBlob` 。  
  
 `pulCodeRVA`  
 擴展成員之相對虛擬位址的指標。  
  
 `pdwImplFlags`  
 擴展與成員相關聯的任何方法執行旗標。  
  
 `pdwCPlusTypeFlag`  
 擴展標記的旗標 <xref:System.ValueType> 。 這是其中一個 `ELEMENT_TYPE_*` 值。
  
 `ppValue`  
 擴展這個成員所傳回的常數位串值。  
  
 `pcchValue`  
 擴展的大小（以字元為單位 `ppValue` ），如果不包含字串，則為零 `ppValue` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
