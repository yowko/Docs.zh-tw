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
ms.openlocfilehash: f577e9252d97ec188ff1076fd8340336b16c8257
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504325"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent 介面
提供[IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md)方法，它會在使用[ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)方法呼叫註冊的事件上執行回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnEvent 方法](iactiononclrevent-onevent-method.md)|針對已註冊的事件執行回呼。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrEvent 列舉](eclrevent-enumeration.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLROnEventManager 介面](iclroneventmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
