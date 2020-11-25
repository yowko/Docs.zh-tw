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
ms.openlocfilehash: 92503df60ae44dfd44819fe3eda8e6a0549b2b66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720982"
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
 [in，out]列舉值的指標。  
  
 `cl`  
 在表示要列舉其成員之類型的 TypeDef 標記。  
  
 `rMembers`  
 擴展用來保存 MemberDef 標記的陣列。  
  
 `cMax`  
 [in] `rMembers` 陣列的大小上限。  
  
 `pcTokens`  
 擴展在中傳回的 MemberDef token 的實際數目 `rMembers` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` 傳回成功。|  
|`S_FALSE`|沒有要列舉的 MemberDef 權杖。 在此情況下， `pcTokens` 是零。|  
  
## <a name="remarks"></a>備註  

 列舉類別的成員集合時， `EnumMembers` 只會傳回 (欄位和方法的成員，而 **不** 是直接在類別上定義的屬性或事件) 。 它不會傳回類別所繼承的任何成員，即使類別提供這些繼承成員的實作為。 若要列舉繼承的成員，呼叫端必須明確地引導繼承鏈。 請注意，繼承鏈的規則可能會根據發出原始中繼資料的語言或編譯器而有所不同。

 不會列舉屬性和事件 `EnumMembers` 。 若要列舉這些，請使用 [EnumProperties](imetadataimport-enumproperties-method.md) 或 [EnumEvents](imetadataimport-enumevents-method.md)。
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
