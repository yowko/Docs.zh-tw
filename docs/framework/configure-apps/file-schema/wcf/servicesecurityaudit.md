---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 10888f26053014ffb1fec49d1dfe87c7fd09ab54
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399583"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
指定在服務作業期間啟用安全性事件稽核的設定。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceSecurityAudit >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|auditLogLocation|指定稽核記錄檔的位置。 有效值包括以下的值：<br /><br /> 預設安全性事件會寫入 Windows XP 上的應用程式記錄檔，以及 Windows Server 2003 和 Windows Vista 上的事件記錄檔。<br />應用程式Audit 事件會寫入至應用程式事件記錄檔。<br />安全級Audit 事件會寫入至安全性事件記錄檔。<br /><br /> 預設值為 Default。 如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLogLocation>。|  
|suppressAuditFailure|布林值，指定隱藏寫入稽核記錄檔錯誤的行為。<br /><br /> 應用程式應會收到稽核記錄檔寫入失敗的通知。 如果您的應用程式不是設計用來處理稽核失敗，應使用這個屬性來隱藏稽核記錄檔的寫入失敗。<br /><br /> 如果這個屬性是 `true`，則 OutOfMemoryException、StackOverFlowException、ThreadAbortException 和 ArgumentException 以外的例外狀況會由系統處理，而不會傳播至應用程式；這些例外狀況是因為嘗試寫入稽核事件所造成的。 如果這個屬性是 `false`，則所有因嘗試寫入稽核事件而造成的例外狀況都會向上傳遞至應用程式。<br /><br /> 預設為 `true`。|  
|serviceAuthorizationAuditLevel|指定記錄在稽核記錄檔中的授權事件類型。 有效值包括以下的值：<br /><br /> 無不會執行任何服務授權事件的審核。<br />Success只會審核成功的服務授權事件。<br />出只會審核失敗的服務授權事件。<br />- SuccessOrFailure:成功和失敗的服務授權事件都會進行審核。<br /><br /> 預設值為 None。 如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLevel>。|  
|messageAuthenticationAuditLevel|指定稽核事件記錄的訊息驗證類型。 有效值包括以下的值：<br /><br /> 無不會產生任何 audit 事件。<br />Success只會記錄成功的安全性（包括訊息簽章驗證、加密和權杖驗證的完整驗證）事件。<br />出只會記錄失敗的事件。<br />- SuccessOrFailure:成功和失敗事件都會記錄下來。<br /><br /> 預設值為 None。 如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLevel>。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 此設定元素用來審查 Windows Communication Foundation （WCF）驗證事件。 啟用稽核時，可以稽核成功或失敗的驗證嘗試 (或兩者)。 事件會寫入三個事件記錄檔之一：應用程式、安全性或作業系統版本的預設記錄檔。 使用 Windows 事件檢視器，即可檢視所有的事件記錄。  
  
 如需使用此設定元素的詳細範例，請參閱[服務的審核行為](../../../wcf/samples/service-auditing-behavior.md)。  
  
 根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。 將 `auditLogLocation` 屬性設定為 'Application' 或 'Security'，即可指定稽核事件的位置。 如需詳細資訊，請參閱[如何：Audit Security 事件](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)。 如果事件是在安全性記錄檔中寫入，則應該將 [LocalSecurityPolicy-> 啟用物件存取] 設定為 [成功] 和 [失敗]。  
  
 在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。 訊息驗證稽核記錄的分類為 "MessageAuthentication"，而服務驗證稽核記錄的分類則為 'ServiceAuthorization'。  
  
 訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。 這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。  
  
 服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。 它們會提供授權是否成功或失敗的相關資訊，以及用戶端的身分識別、訊息傳送到的端點、與訊息相關聯的動作，以及從內送訊息，以及做出存取決策的授權管理員類型。  
  
## <a name="example"></a>範例  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [安全性行為](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [稽核](../../../wcf/feature-details/auditing-security-events.md)
- [如何：Audit Security 事件](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [服務稽核行為](../../../wcf/samples/service-auditing-behavior.md)
