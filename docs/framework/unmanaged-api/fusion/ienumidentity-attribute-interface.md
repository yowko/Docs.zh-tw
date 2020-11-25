---
title: IEnumIDENTITY_ATTRIBUTE 介面
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: 71a6ea9f593da093985a4420e690f1bdd7f9d139
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728988"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE 介面

作為目前範圍中程式碼物件之屬性的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|取得新的介面指標， `IEnumIDENTITY_ATTRIBUTE` 其中包含與這個相同的成員 `IEnumIDENTITY_ATTRIBUTE` 。|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|將此專案中包含的資料寫入 `IEnumIDENTITY_ATTRIBUTE` 至指定的資料緩衝區。|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|從目前位置開始取得指定數目的屬性。|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|將指令指標移至這個的開頭 `IEnumIDENTITY_ATTRIBUTE` 。|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|從目前位置開始，將指令指標向下移動指定數目的元素。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
