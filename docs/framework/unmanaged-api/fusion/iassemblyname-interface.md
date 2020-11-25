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
ms.openlocfilehash: f6feed9f59715f9a2801cd3a2a99a087957d4377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715065"
---
# <a name="iassemblyname-interface"></a>IAssemblyName 介面

提供用來描述和使用元件唯一身分識別的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](iassemblyname-clone-method.md)|建立這個物件的淺層複本 `IAssemblyName` 。|  
|[Finalize 方法](iassemblyname-finalize-method.md)|允許這個 `IAssemblyName` 物件釋放資源並執行其他清除作業，然後再呼叫它的函式。|  
|[GetDisplayName 方法](iassemblyname-getdisplayname-method.md)|取得這個物件所參考之元件的人類可讀取名稱 `IAssemblyName` 。|  
|[GetName 方法](iassemblyname-getname-method.md)|取得這個物件所參考之元件的簡單、未加密的名稱 `IAssemblyName` 。|  
|[GetProperty 方法](iassemblyname-getproperty-method.md)|取得指定之所參考之屬性的指標 `PropertyId` 。|  
|[GetVersion 方法](iassemblyname-getversion-method.md)|取得這個物件所參考之元件的版本資訊 `IAssemblyName` 。|  
|[IsEqual 方法](iassemblyname-isequal-method.md)|`IAssemblyName` `IAssemblyName` 根據指定的比較旗標，判斷指定的物件是否等於這個。|  
|[SetProperty 方法](iassemblyname-setproperty-method.md)|設定指定之所參考屬性的值 `PropertyId` 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合介面](fusion-interfaces.md)
- [IAssemblyEnum 介面](iassemblyenum-interface.md)
