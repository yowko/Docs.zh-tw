---
title: IAssemblyName 介面
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697923"
---
# <a name="iassemblyname-interface"></a>IAssemblyName 介面
提供方法來描述和使用組件的唯一身分識別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|建立這個的淺層複製`IAssemblyName`物件。|  
|[Finalize 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|這可讓`IAssemblyName`物件釋放資源並呼叫其解構函式之前執行其他清除作業。|  
|[GetDisplayName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|取得人類可讀名稱所參考的組件`IAssemblyName`物件。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|取得所參考的組件的簡單且未加密名稱`IAssemblyName`物件。|  
|[GetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|取得所指定參考之屬性的指標`PropertyId`。|  
|[GetVersion 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|取得所參考的組件的版本資訊`IAssemblyName`物件。|  
|[IsEqual 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|判斷指定`IAssemblyName`物件是否等於這個`IAssemblyName`，根據指定的比較旗標。|  
|[SetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|設定所指定參考之屬性的值`PropertyId`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
