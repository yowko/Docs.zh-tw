---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102930"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>語法  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceAuthorizationBehavior 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceAuthorizationBehavior 類別具有下列屬性：  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 值，控制服務是否使用傳入訊息所提供的認證來嘗試模擬。  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於在伺服器上執行作業的原則。  
  
### <a name="roleprovider"></a>RoleProvider  
 資料型別：字串  
  
 存取類型：唯讀  
  
 ASP.NET 角色提供者的名稱。  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於自訂授權的授權管理員。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
