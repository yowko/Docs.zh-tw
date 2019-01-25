---
title: IMetaDataEmit::DefineTypeRefByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dd08afba664a491b3ba398f3da4c6a73cda5378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517132"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName 方法
取得定義在指定的範圍內，也就是目前範圍以外的類型中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>參數  
 `tkResolutionScope`  
 [in]指定的解析範圍語彙基元。 下列的語彙基元型別是有效的：  
  
-   `mdModuleRef`如果呼叫端定義所在的相同組件中定義型別。  
  
-   `mdAssemblyRef`如果不同於呼叫端定義的組件中定義的類型。  
  
-   `mdTypeRef`如果類型是巢狀型別。  
  
-   `mdModule`如果類型定義在呼叫端定義所在的相同模組中。  
  
-   如果為 null，全域定義類型。  
  
 `szName`  
 [in]以 Unicode 的目標類型的名稱。  
  
 `ptr`  
 [out]指標`mdTypeRef`指派給類型的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
