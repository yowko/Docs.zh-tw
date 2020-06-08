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
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492729"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps 方法
針對指定之標記所參考的泛型參數定義，設定屬性值。  
  
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
 在要為其設定值之泛型參數定義的 token。  
  
 `dwParamFlags`  
 在[CorGenericParamAttr](corgenericparamattr-enumeration.md)列舉的值，描述泛型參數的類型。  
  
 `szName`  
 [in] 選用。 要設定值的參數名稱。  
  
 `reserved`  
 在保留以供未來擴充性之用。  
  
 `rtkConstraints`  
 [in] 選用。 類型條件約束之以零結束的陣列。 陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
