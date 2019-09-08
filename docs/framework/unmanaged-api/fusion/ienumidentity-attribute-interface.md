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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796461"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE 介面
作為目前範圍中程式碼物件屬性的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|取得新`IEnumIDENTITY_ATTRIBUTE`的介面指標，其中包含與這個`IEnumIDENTITY_ATTRIBUTE`相同的成員。|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|將此`IEnumIDENTITY_ATTRIBUTE`專案中包含的資料寫入指定的資料緩衝區。|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|取得指定數目的屬性，從目前位置開始。|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|將指令指標移至這個`IEnumIDENTITY_ATTRIBUTE`的開頭。|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|從目前位置開始，將指令指標向下移動指定的專案數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
