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
ms.openlocfilehash: bea357fe9a154ffb8f69228c7332c026dc2759e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728964"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity 介面

作為物件集合的列舉值 `IReferenceIdentity` 。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|取得新的介面指標， `IEnumReferenceIdentity` 其中包含與這個相同的成員 `IEnumReferenceIdentity` 。|  
|`IEnumReferenceIdentity::Next`|`IReferenceIdentity`從目前位置開始取得指定數目的物件。|  
|`IEnumReferenceIdentity::Reset`|將指令指標移至這個的開頭 `IEnumReferenceIdentity` 。|  
|`IEnumReferenceIdentity::Skip`|從目前位置開始，將指令指標向下移動指定數目的元素。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IReferenceIdentity 介面](ireferenceidentity-interface.md)
