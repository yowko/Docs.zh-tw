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
ms.openlocfilehash: 5c2880ac07f0317bc36ff4bbde68cd3a25febf52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721981"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps 方法

設定或更新由先前呼叫 [IMetaDataEmit：:D efineevent](imetadataemit-defineevent-method.md)所定義之事件的指定功能。  
  
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
 在事件標記。  
  
 `dwEventFlags`  
 在事件旗標。 這是值的位元遮罩 `CorEventAttr` 。  
  
 `tkEventType`  
 在事件類別的 token。 這可能是 `mdTypeDef` 或 `mdTypeRef` 標記。  
  
 `mdAddOn`  
 在用來訂閱事件的方法，或 null。  
  
 `mdRemoveOn`  
 在用來取消訂閱事件的方法，或 null。  
  
 `mdFire`  
 在衍生類別 (使用的方法) 來引發事件。  
  
 `rmdOtherMethods[]`  
 在與事件相關聯之其他方法的標記陣列。 陣列的最後一個元素必須是 `mdMethodDefNil` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
