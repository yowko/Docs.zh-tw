---
title: IMetaDataEmit::SetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450327"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps 方法
設定或更新先前呼叫[IMetaDataEmit：:D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)所定義之事件的指定功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>參數  
 `ev`  
 在事件 token。  
  
 `dwEventFlags`  
 在事件旗標。 這是 `CorEventAttr` 值的位元遮罩。  
  
 `tkEventType`  
 在事件類別的 token。 這可以是 `mdTypeDef` 或 `mdTypeRef` token。  
  
 `mdAddOn`  
 在用來訂閱事件的方法，或 null。  
  
 `mdRemoveOn`  
 在用來取消訂閱事件的方法，或 null。  
  
 `mdFire`  
 在用來引發事件的方法（由衍生類別）。  
  
 `rmdOtherMethods[]`  
 在與事件相關聯之其他方法的權杖陣列。 陣列的最後一個元素必須 `mdMethodDefNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
