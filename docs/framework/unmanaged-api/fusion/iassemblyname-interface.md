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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796547"
---
# <a name="iassemblyname-interface"></a>IAssemblyName 介面
提供方法來描述和使用元件的唯一身分識別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](iassemblyname-clone-method.md)|建立這個`IAssemblyName`物件的淺層複本。|  
|[Finalize 方法](iassemblyname-finalize-method.md)|允許此`IAssemblyName`物件釋放資源，並執行其他清除作業，再呼叫其析構函式。|  
|[GetDisplayName 方法](iassemblyname-getdisplayname-method.md)|取得這個`IAssemblyName`物件所參考之元件的人類可讀名稱。|  
|[GetName 方法](iassemblyname-getname-method.md)|取得這個`IAssemblyName`物件所參考的簡單、未加密的元件名稱。|  
|[GetProperty 方法](iassemblyname-getproperty-method.md)|取得指定`PropertyId`之所參考之屬性的指標。|  
|[GetVersion 方法](iassemblyname-getversion-method.md)|取得這個`IAssemblyName`物件所參考之元件的版本資訊。|  
|[IsEqual 方法](iassemblyname-isequal-method.md)|根據指定的比較`IAssemblyName`旗標，判斷指定`IAssemblyName`的物件是否等於這個。|  
|[SetProperty 方法](iassemblyname-setproperty-method.md)|設定指定`PropertyId`之所參考之屬性的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IAssemblyEnum 介面](iassemblyenum-interface.md)
