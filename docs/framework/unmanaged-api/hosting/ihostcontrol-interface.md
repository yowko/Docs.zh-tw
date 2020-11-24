---
title: IHostControl 介面
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 1bffef31702aa051d9ca865b18a67ac90c00cd00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680650"
---
# <a name="ihostcontrol-interface"></a>IHostControl 介面

提供方法來設定元件的載入，以及判斷主機所支援的裝載介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetHostManager 方法](ihostcontrol-gethostmanager-method.md)|取得具有指定之介面的主機實介面指標 `IID` 。|  
|[SetAppDomainManager 方法](ihostcontrol-setappdomainmanager-method.md)|通知主機已建立應用程式域。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
