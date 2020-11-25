---
title: IActionOnCLREvent 介面
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 8ca4bb1fe35451f95f752a4e71f5f0b541b55e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721773"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent 介面

提供 [IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md) 方法，該方法會在已使用 [ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 方法呼叫註冊的事件上執行回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnEvent 方法](iactiononclrevent-onevent-method.md)|針對已註冊的事件執行回呼。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrEvent 列舉](eclrevent-enumeration.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLROnEventManager 介面](iclroneventmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
