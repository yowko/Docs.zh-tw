---
title: <serviceAuthorization> 項目
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834015"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="3146b-102">\<serviceAuthorization> 項目</span><span class="sxs-lookup"><span data-stu-id="3146b-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="3146b-103">指定設定，這些設定會將存取權授權給服務作業。</span><span class="sxs-lookup"><span data-stu-id="3146b-103">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="3146b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3146b-104">Syntax</span></span>

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3146b-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3146b-105">Attributes and elements</span></span>

<span data-ttu-id="3146b-106">下列各節說明屬性、子項目和父元素：</span><span class="sxs-lookup"><span data-stu-id="3146b-106">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="3146b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3146b-107">Attributes</span></span>

|<span data-ttu-id="3146b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3146b-108">Attribute</span></span>|<span data-ttu-id="3146b-109">描述</span><span class="sxs-lookup"><span data-stu-id="3146b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3146b-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="3146b-110">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="3146b-111">布林值，指定服務中所有作業是否都模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3146b-111">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="3146b-112">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3146b-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3146b-113">當特定服務作業模擬呼叫端時，執行緒內容會在執行指定的服務之前切換為呼叫端內容。</span><span class="sxs-lookup"><span data-stu-id="3146b-113">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="3146b-114">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="3146b-114">principalPermissionMode</span></span>|<span data-ttu-id="3146b-115">設定用於在伺服器上執行作業的原則。</span><span class="sxs-lookup"><span data-stu-id="3146b-115">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="3146b-116">包括下列值：</span><span class="sxs-lookup"><span data-stu-id="3146b-116">Values include the following:</span></span><br /><br /> <span data-ttu-id="3146b-117">-無</span><span class="sxs-lookup"><span data-stu-id="3146b-117">-   None</span></span><br /><span data-ttu-id="3146b-118">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="3146b-118">-   UseWindowsGroups</span></span><br /><span data-ttu-id="3146b-119">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="3146b-119">-   UseAspNetRoles</span></span><br /><span data-ttu-id="3146b-120">-Custom</span><span class="sxs-lookup"><span data-stu-id="3146b-120">-   Custom</span></span><br /><br /> <span data-ttu-id="3146b-121">預設值為 UseWindowsGroups。</span><span class="sxs-lookup"><span data-stu-id="3146b-121">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="3146b-122">此值的型別為 <xref:System.ServiceModel.Description.PrincipalPermissionMode>。</span><span class="sxs-lookup"><span data-stu-id="3146b-122">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="3146b-123">如需使用此屬性的詳細資訊，請參閱 how [to：使用 PrincipalPermissionAttribute 類別來限制存取](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。</span><span class="sxs-lookup"><span data-stu-id="3146b-123">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="3146b-124">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="3146b-124">roleProviderName</span></span>|<span data-ttu-id="3146b-125">字串，指定角色提供者的名稱，它會提供 Windows Communication Foundation (WCF) 應用程式的角色資訊。</span><span class="sxs-lookup"><span data-stu-id="3146b-125">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="3146b-126">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="3146b-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="3146b-127">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="3146b-127">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="3146b-128">字串，其中包含服務授權管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="3146b-128">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="3146b-129">如需詳細資訊，請參閱 <xref:System.ServiceModel.ServiceAuthorizationManager> 。</span><span class="sxs-lookup"><span data-stu-id="3146b-129">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="3146b-130">子元素</span><span class="sxs-lookup"><span data-stu-id="3146b-130">Child elements</span></span>

|<span data-ttu-id="3146b-131">元素</span><span class="sxs-lookup"><span data-stu-id="3146b-131">Element</span></span>|<span data-ttu-id="3146b-132">描述</span><span class="sxs-lookup"><span data-stu-id="3146b-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3146b-133">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="3146b-133">authorizationPolicies</span></span>|<span data-ttu-id="3146b-134">包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。</span><span class="sxs-lookup"><span data-stu-id="3146b-134">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="3146b-135">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="3146b-135">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="3146b-136">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="3146b-136">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3146b-137">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="3146b-137">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="3146b-138">如需詳細資訊，請參閱 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement> 。</span><span class="sxs-lookup"><span data-stu-id="3146b-138">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="3146b-139">父元素</span><span class="sxs-lookup"><span data-stu-id="3146b-139">Parent elements</span></span>

|<span data-ttu-id="3146b-140">元素</span><span class="sxs-lookup"><span data-stu-id="3146b-140">Element</span></span>|<span data-ttu-id="3146b-141">描述</span><span class="sxs-lookup"><span data-stu-id="3146b-141">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3146b-142">包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="3146b-142">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="3146b-143">備註</span><span class="sxs-lookup"><span data-stu-id="3146b-143">Remarks</span></span>

<span data-ttu-id="3146b-144">本章節包含會影響授權的項目、自訂的角色提供者，以及模擬。</span><span class="sxs-lookup"><span data-stu-id="3146b-144">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="3146b-145">`principalPermissionMode` 屬性會指定要在授權使用保護的方法時使用的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="3146b-145">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="3146b-146">預設值為 `UseWindowsGroups`，其指定了在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。</span><span class="sxs-lookup"><span data-stu-id="3146b-146">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="3146b-147">您也可以指定使用在專案底下 `UseAspNetRoles` 設定的自訂角色提供者 \<system.web> ，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="3146b-147">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
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
  <!-- Other configuration code not shown. -->
</system.web>
```
  
<span data-ttu-id="3146b-148">下列程式碼顯示 `roleProviderName` 與屬性搭配使用的 `principalPermissionMode` ：</span><span class="sxs-lookup"><span data-stu-id="3146b-148">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="3146b-149">如需使用此 configuration 元素的詳細範例，請參閱[授權存取服務作業](../../../wcf/samples/authorizing-access-to-service-operations.md)和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="3146b-149">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3146b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3146b-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="3146b-151">安全性行為</span><span class="sxs-lookup"><span data-stu-id="3146b-151">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3146b-152">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="3146b-152">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="3146b-153">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="3146b-153">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="3146b-154">如何：利用 PrincipalPermissionAttribute 類別限制存取</span><span class="sxs-lookup"><span data-stu-id="3146b-154">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="3146b-155">授權原則</span><span class="sxs-lookup"><span data-stu-id="3146b-155">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
