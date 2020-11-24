---
title: ICLRDomainManager 介面
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: a5abb601fe795a0c615403eec69f68ad9f66f00f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681167"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager 介面

讓主機指定將用來初始化預設應用程式域的應用程式域管理員，以及指定初始化屬性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetAppDomainManagerType 方法](iclrdomainmanager-setappdomainmanagertype-method.md)|指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域的應用程式域管理員型別，衍生自類別。|  
|[SetPropertiesForDefaultAppDomain 方法](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|設定將用來初始化預設應用程式域的屬性。|  
  
## <a name="remarks"></a>備註  

 若要取得這個介面的實例，請使用管理員類型 IID 來呼叫 [ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md) 方法 `IID_ICLRDomainManager` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
