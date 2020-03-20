---
title: IMetaDataImport::EnumMembersWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177324"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName 方法
列舉 MemberDef 語彙基元，其代表具有指定名稱之指定類型成員。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。  
  
 `cl`  
 [在]表示要枚舉的成員的類型的類型的類型的類型類型。  
  
 `szName`  
 [在]限制枚舉器範圍的成員名稱。  
  
 `rMembers`  
 [出]用於存儲成員Def權杖的陣列。  
  
 `cMax`  
 [in] `rMembers` 陣列的大小上限。  
  
 `pcTokens`  
 [出]在 中`rMembers`返回的會員Def權杖的實際數量。  
  
## <a name="remarks"></a>備註  
 此方法枚舉欄位和方法，但不枚舉屬性或事件。 與[IMetaDataImport：：enum成員](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)不同，`EnumMembersWithName`請丟棄沒有指定名稱的所有欄位和成員權杖。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`已成功返回。|  
|`S_FALSE`|沒有要枚舉的會員Def權杖。 在這種情況下，`pcTokens`為零。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
