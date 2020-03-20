---
title: IMetaDataEmit::SetTypeDefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177468"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps 方法
設置以前調用[IMetaDataEmit：:DefineTypeDef）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)定義的類型的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 [在]從`mdTypeDef`原始調用[IMetaDataEmit 獲得權杖：:DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。  
  
 `dwTypeDefFlags`  
 [在]`TypeDef`屬性。 這是值的`CorTypeAttr`位元遮罩。  
  
 `tkExtends`  
 [在]基`mdToken`類的 。 從之前對[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)的調用中獲取：:Define`null`導入類型，或 。  
  
 `rtkImplements[]`  
 [在]此類型實現的介面的權杖陣列。 這些`mdTypeRef`權杖是使用[IMetaDataEmit：:Define 導入類型](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)獲得的。 陣列的最後一個元素必須是`mdTokenNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
