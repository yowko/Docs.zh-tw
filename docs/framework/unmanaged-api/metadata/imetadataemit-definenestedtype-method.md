---
title: IMetaDataEmit::DefineNestedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175807"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType 方法
創建類型定義的中繼資料簽名，返回該類型的`mdTypeDef`權杖，並指定定義的類型是`tdEncloser`參數引用的類型的成員。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>參數  
 `szTypeDef`  
 [在]Unicode 中類型的名稱。  
  
 `dwTypeDefFlags`  
 [在]`TypeDef`屬性。 這是值的`CorTypeAttr`位元遮罩。  
  
 `tkExtends`  
 [在]基類的權杖。 這是 或`mdTypeDef``mdTypeRef`標記。  
  
 `rtkImplements`[]  
 [在]指定此類或介面實現的介面的權杖陣列。  
  
 `tdEncloser`  
 [在]封閉類型的標記。 陣列的最後一個元素必須是`mdTokenNil`。  
  
 `ptd`  
 [出]分配的`mdTypeDef`權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
