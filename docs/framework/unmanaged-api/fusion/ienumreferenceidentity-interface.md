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
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697247"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity 介面
做為集合的列舉程式`IReferenceIdentity`物件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|取得新的介面指標`IEnumReferenceIdentity`，其中包含與這個相同的成員`IEnumReferenceIdentity`。|  
|`IEnumReferenceIdentity::Next`|取得指定的數目`IReferenceIdentity`物件，從目前位置開始。|  
|`IEnumReferenceIdentity::Reset`|將指令指標移至這個開頭`IEnumReferenceIdentity`。|  
|`IEnumReferenceIdentity::Skip`|將指令指標向前移的指定項目數，從目前位置開始。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Isolation.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IReferenceIdentity 介面](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
