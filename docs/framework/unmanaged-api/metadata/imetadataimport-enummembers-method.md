---
title: IMetaDataImport::EnumMembers 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175482"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers 方法
列舉代表指定類型成員的 MemberDef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。  
  
 `cl`  
 [在]表示要枚舉其成員的類型的類型的類型的類型。  
  
 `rMembers`  
 [出]用於保存成員Def權杖的陣列。  
  
 `cMax`  
 [in] `rMembers` 陣列的大小上限。  
  
 `pcTokens`  
 [出]在 中`rMembers`返回的會員Def權杖的實際數量。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`已成功返回。|  
|`S_FALSE`|沒有要枚舉的會員Def權杖。 在這種情況下，`pcTokens`為零。|  
  
## <a name="remarks"></a>備註  
 枚舉類成員的集合時，`EnumMembers`僅返回直接在類上定義的成員（欄位和方法，**但不包括**屬性或事件）。 它不返回類繼承的任何成員，即使類為這些繼承成員提供了實現也是如此。 要枚舉繼承的成員，調用方必須顯式遍歷繼承鏈。 請注意，繼承鏈的規則可能因發出原始中繼資料的語言或編譯器而異。

 屬性和事件不由 枚舉`EnumMembers`枚舉。 要枚舉這些，請使用[枚舉屬性](imetadataimport-enumproperties-method.md)或[枚舉事件](imetadataimport-enumevents-method.md)。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
