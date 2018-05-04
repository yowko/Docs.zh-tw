---
title: '&lt;serviceAuthorization&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: cd5cb072f424927615b6e87d9193a9c200a8c48b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceauthorizationgt-element"></a>&lt;serviceAuthorization&gt; 項目
指定設定，這些設定會將存取權授權給服務作業。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<serviceAuthorization >  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|布林值，指定服務中所有作業是否都模擬呼叫端。 預設為 `false`。<br /><br /> 當特定服務作業模擬呼叫端時，執行緒內容會在執行指定的服務之前切換為呼叫端內容。|  
|principalPermissionMode|設定用於在伺服器上執行作業的原則。 包括下列值：<br /><br /> -無<br />-UseWindowsGroups<br />-UseAspNetRoles<br />自訂<br /><br /> 預設值為 UseWindowsGroups。 此值的型別為 <xref:System.ServiceModel.Description.PrincipalPermissionMode>。 如需有關如何使用這個屬性的詳細資訊，請參閱[How to： 使用 PrincipalPermissionAttribute 類別的限制存取](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。|  
|roleProviderName|字串，指定角色提供者的名稱，它會提供 Windows Communication Foundation (WCF) 應用程式的角色資訊。 預設為空字串。|  
|ServiceAuthorizationManagerType|字串，其中包含服務授權管理員的型別。 如需詳細資訊，請參閱<xref:System.ServiceModel.ServiceAuthorizationManager>。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|authorizationPolicies|包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。 每個授權原則包含一個必要的 `policyType` 屬性字串。 該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。 它可以做為授與或拒絕存取控制 (Access Control) 的基礎。 如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|包含服務行為之設定的集合。|  
  
## <a name="remarks"></a>備註  
 本章節包含會影響授權的項目、自訂的角色提供者，以及模擬。  
  
 `principalPermissionMode` 屬性會指定要在授權使用保護的方法時使用的使用者群組。 預設值為 `UseWindowsGroups`，其指定了在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。 您也可以指定`UseAspNetRoles`使用自訂角色提供者設定下\<system.web > 項目，如下列程式碼所示。  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 下列程式碼示範搭配 `roleProviderName` 屬性使用的 `principalPermissionMode`。  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 使用這個組態項目詳細範例，請參閱[授權存取服務作業](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)和[授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [授權存取服務作業](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [如何：為服務建立自訂授權管理員](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [如何：利用 PrincipalPermissionAttribute 類別限制存取](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [授權原則](../../../../../docs/framework/wcf/samples/authorization-policy.md)
