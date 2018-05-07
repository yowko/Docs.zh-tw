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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ee8c62861a62ac044f295f7da082756d87347b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers 方法
列舉代表指定類型成員的 MemberDef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。  
  
 `cl`  
 [in]代表其成員的列舉的類型的 TypeDef 語彙基元。  
  
 `rMembers`  
 [out]陣列，用來保存 memberdef 語彙基元。  
  
 `cMax`  
 [in] `rMembers` 陣列的大小上限。  
  
 `pcTokens`  
 [out]Memberdef 語彙基元中傳回的實際數目`rMembers`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` 已成功傳回。|  
|`S_FALSE`|沒有列舉 MemberDef 語彙基元。 在此情況下，`pcTokens`為零。|  
  
## <a name="remarks"></a>備註  
 列舉集合成員的類別，當`EnumMembers`傳回直接在類別上定義的成員。 即使類別會實作提供這些繼承的成員，它不會傳回此類別會繼承，任何成員。 若要列舉繼承的成員，呼叫端必須明確地逐步繼承鏈結。 請注意，規則的繼承鏈結會視語言或編譯器發出的原始中繼資料。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
