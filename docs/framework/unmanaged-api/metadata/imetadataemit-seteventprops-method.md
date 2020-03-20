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
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177533"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps 方法
設置或更新由之前調用[IMetaDataEmit：:DefineEvent）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)定義的事件的指定功能。  
  
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
 [在]事件權杖。  
  
 `dwEventFlags`  
 [在]事件標誌。 這是值的`CorEventAttr`位元遮罩。  
  
 `tkEventType`  
 [在]事件類的權杖。 這是 或`mdTypeDef``mdTypeRef`標記。  
  
 `mdAddOn`  
 [在]用於訂閱事件或 null 的方法。  
  
 `mdRemoveOn`  
 [在]用於取消訂閱事件或 null 的方法。  
  
 `mdFire`  
 [在]用於（由派生類）引發事件的方法。  
  
 `rmdOtherMethods[]`  
 [在]與事件關聯的其他方法的權杖陣列。 陣列的最後一個元素必須是`mdMethodDefNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
