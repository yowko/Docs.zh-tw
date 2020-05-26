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
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804927"
---
# <a name="ihostcontrol-interface"></a>IHostControl 介面
提供設定元件載入的方法，以及判斷主機支援的主控介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetHostManager 方法](ihostcontrol-gethostmanager-method.md)|取得具有指定之之介面的主機介面指標 `IID` 。|  
|[SetAppDomainManager 方法](ihostcontrol-setappdomainmanager-method.md)|通知主機已建立應用程式域。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
