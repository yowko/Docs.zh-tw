---
title: IMetaDataEmit::DefineEvent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 7babd0a90b9882acb03b6360753f55c57a399b9e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005620"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent 方法
使用指定的中繼資料簽章建立事件的定義，並取得該事件定義的 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 在目標類別或介面的 token。 這可能是 `mdTypeDef` 或 `mdTypeDefNil` token。  
  
 `szEvent`  
 在事件的名稱。  
  
 `dwEventFlags`  
 在事件旗標。  
  
 `tkEventType`  
 在事件類別的 token。 這是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTokenNil` 權杖。  
  
 `mdAddOn`  
 在用來訂閱事件的方法，或 null。  
  
 `mdRemoveOn`  
 在用來取消訂閱事件的方法，或 null。  
  
 `mdFire`  
 在用來引發事件的方法（由衍生類別）。  
  
 `rmdOtherMethods[]`  
 在與事件相關聯之其他方法的權杖陣列。 陣列以 `mdMethodDefNil` 標記終止。  
  
 `pmdEvent`  
 脫銷指派給事件的元資料標記。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
