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
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615705"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager 介面
可讓主機指定將用來初始化預設應用程式域的應用程式網域管理員，以及指定初始化屬性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetAppDomainManagerType 方法](iclrdomainmanager-setappdomainmanagertype-method.md)|指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域之應用程式網域管理員的類型（衍生自類別）。|  
|[SetPropertiesForDefaultAppDomain 方法](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|設定將用來初始化預設應用程式域的屬性。|  
  
## <a name="remarks"></a>備註  
 若要取得此介面的實例，請使用 manager 類型 IID 呼叫[ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md)方法 `IID_ICLRDomainManager` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
