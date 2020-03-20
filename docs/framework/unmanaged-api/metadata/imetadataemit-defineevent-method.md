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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175846"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent 方法
為具有指定中繼資料簽名的事件創建定義，並獲取該事件定義的權杖。  
  
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
 [在]目標類或介面的權杖。 這是 或`mdTypeDef``mdTypeDefNil`標記。  
  
 `szEvent`  
 [在]事件的名稱。  
  
 `dwEventFlags`  
 [在]事件標誌。  
  
 `tkEventType`  
 [在]事件類的權杖。 這是 一`mdTypeDef`個`mdTypeRef`、或`mdTokenNil`標記。  
  
 `mdAddOn`  
 [在]用於訂閱事件或 null 的方法。  
  
 `mdRemoveOn`  
 [在]用於取消訂閱事件或 null 的方法。  
  
 `mdFire`  
 [在]用於（由派生類）引發事件的方法。  
  
 `rmdOtherMethods[]`  
 [在]與事件關聯的其他方法的權杖陣列。 陣列用`mdMethodDefNil`權杖終止。  
  
 `pmdEvent`  
 [出]分配給事件的中繼資料權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
