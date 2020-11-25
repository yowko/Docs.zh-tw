---
title: IMetaDataEmit2::SetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8858e692d66f7b34a66334bd4e8b906dd12962ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701987"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps 方法

設定指定之標記所參考之泛型參數定義的屬性值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>參數  

 `gp`  
 在要設定其值之泛型參數定義的標記。  
  
 `dwParamFlags`  
 在描述泛型參數之類型的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 列舉值。  
  
 `szName`  
 [in] 選用。 要設定其值的參數名稱。  
  
 `reserved`  
 在保留供未來擴充性之用。  
  
 `rtkConstraints`  
 [in] 選用。 以零結束的型別條件約束陣列。 陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
