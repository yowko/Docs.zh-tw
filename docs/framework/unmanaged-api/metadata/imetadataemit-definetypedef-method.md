---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175755"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法
為通用語言運行時類型創建類型定義，並獲取該類型定義的中繼資料權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>參數  
 `szTypeDef`  
 [在]Unicode 中類型的名稱。  
  
 `dwTypeDefFlags`  
 [在]`TypeDef`屬性。 這是值的`CoreTypeAttr`位元遮罩。  
  
 `tkExtends`  
 [在]基類的權杖。 它必須是 或`mdTypeDef``mdTypeRef`標記。  
  
 `rtkImplements`  
 [在]指定此類或介面實現的介面的權杖陣列。  
  
 `ptd`  
 [出]分配的`mdTypeDef`權杖。  
  
## <a name="remarks"></a>備註  
 中`dwTypeDefFlags`的標誌指定正在創建的類型是公共類型系統參考型別（類或介面）還是公共類型系統數值型別。  
  
 根據提供的參數，此方法作為副作用，還可以為此類型繼承或實現的每個介面創建`mdInterfaceImpl`記錄。 但是，此方法不會返回任何這些`mdInterfaceImpl`權杖。 如果用戶端希望以後添加或修改`mdInterfaceImpl`權杖，則必須使用介面`IMetaDataImport`枚舉它們。 如果要使用介面的`[default]`COM 語義，則應將預設介面作為`rtkImplements`中的第一個元素提供 。類上的自訂屬性集將指示類具有預設介面（始終假定該介面是為類聲明的第一個`mdInterfaceImpl`權杖）。  
  
 `rtkImplements`陣列的每個元素都包含 或`mdTypeDef``mdTypeRef`權杖。 陣列中的最後一個元素必須為`mdTokenNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
