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
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007763"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps 方法
設定先前呼叫 IMetaDataEmit 所定義之類型的功能[：:D efinetypedef](imetadataemit-definetypedef-method.md)。  
  
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
 在`mdTypeDef`從原始呼叫中取得的權杖[IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md)。  
  
 `dwTypeDefFlags`  
 [in] `TypeDef`特性. 這是值的位元遮罩 `CorTypeAttr` 。  
  
 `tkExtends`  
 在`mdToken`基類的。 從先前的 IMetaDataEmit 呼叫取得[：:D efineimporttype](imetadataemit-defineimporttype-method.md)，或 `null` 。  
  
 `rtkImplements[]`  
 在這個類型所執行介面的權杖陣列。 這些 `mdTypeRef` 權杖是使用[IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md)取得。 陣列的最後一個元素必須是 `mdTokenNil` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
