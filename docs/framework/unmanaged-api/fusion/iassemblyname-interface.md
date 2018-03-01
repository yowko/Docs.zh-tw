---
title: "IAssemblyName 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 902ad9f67d06306e79666f0e10d85bdb9c65c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblyname-interface"></a>IAssemblyName 介面
提供方法來描述及使用組件的唯一識別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|建立這樣的淺層複本`IAssemblyName`物件。|  
|[Finalize 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|允許您為此`IAssemblyName`物件釋放資源並呼叫其解構函式之前執行其他清除作業。|  
|[GetDisplayName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|取得人類看得懂的名稱所參考的組件`IAssemblyName`物件。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|取得所參考的組件的簡單、 未加密名稱`IAssemblyName`物件。|  
|[GetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|取得所指定參考之屬性的指標`PropertyId`。|  
|[GetVersion 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|取得所參考的組件的版本資訊`IAssemblyName`物件。|  
|[IsEqual 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|決定指定`IAssemblyName`物件是否等於此`IAssemblyName`，根據指定的比較旗標。|  
|[SetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|設定所指定參考之屬性的值`PropertyId`。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
