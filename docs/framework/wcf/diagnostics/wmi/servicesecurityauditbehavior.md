---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1ce712bbdb258c477a2ee56f47281b1a1d09ec54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>語法  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceSecurityAuditBehavior 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceSecurityAuditBehavior 類別有下列屬性：  
  
### <a name="auditloglocation"></a>AuditLogLocation  
 資料型別：字串  
  
 存取類型：唯讀  
  
 稽核記錄檔的位置。  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於記錄稽核事件之訊息驗證等級的類型。  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 資料型別：字串  
  
 存取類型：唯讀  
  
 稽核記錄檔中記錄之授權事件的類型。  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定隱藏寫入稽核記錄檔錯誤的行為。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
