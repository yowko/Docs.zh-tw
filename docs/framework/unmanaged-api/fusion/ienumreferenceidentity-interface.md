---
title: IEnumReferenceIdentity 介面
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796439"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity 介面
作為物件集合的`IReferenceIdentity`列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|取得新`IEnumReferenceIdentity`的介面指標，其中包含與這個`IEnumReferenceIdentity`相同的成員。|  
|`IEnumReferenceIdentity::Next`|取得指定數目的`IReferenceIdentity`物件，從目前位置開始。|  
|`IEnumReferenceIdentity::Reset`|將指令指標移至這個`IEnumReferenceIdentity`的開頭。|  
|`IEnumReferenceIdentity::Skip`|從目前位置開始，將指令指標向下移動指定的專案數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IReferenceIdentity 介面](ireferenceidentity-interface.md)
