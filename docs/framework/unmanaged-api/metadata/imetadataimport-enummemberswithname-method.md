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
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492066"
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
 [in、out]列舉值的指標。  
  
 `cl`  
 在TypeDef token，代表具有要列舉之成員的類型。  
  
 `szName`  
 在限制列舉值範圍的成員名稱。  
  
 `rMembers`  
 脫銷用來儲存 MemberDef 標記的陣列。  
  
 `cMax`  
 [in] `rMembers` 陣列的大小上限。  
  
 `pcTokens`  
 脫銷在中傳回的 MemberDef token 實際數目 `rMembers` 。  
  
## <a name="remarks"></a>備註  
 這個方法會列舉欄位和方法，而不是屬性或事件。 不同于[IMetaDataImport：： EnumMembers](imetadataimport-enummembers-method.md)，會 `EnumMembersWithName` 捨棄所有沒有指定名稱的欄位和成員 token。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`已成功傳回。|  
|`S_FALSE`|沒有要列舉的 MemberDef token。 在此情況下， `pcTokens` 是零。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
