---
title: <serviceAuthorization> 項目
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834015"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="cdf9e-102">@no__t 0serviceAuthorization > 元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="cdf9e-103">指定設定，這些設定會將存取權授權給服務作業。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="cdf9e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cdf9e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cdf9e-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cdf9e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cdf9e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<behaviors >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cdf9e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cdf9e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cdf9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="cdf9e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0behavior >** ](behavior-of-servicebehaviors.md)1</span><span class="sxs-lookup"><span data-stu-id="cdf9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\</span></span>
<span data-ttu-id="cdf9e-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="cdf9e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="cdf9e-110">語法</span><span class="sxs-lookup"><span data-stu-id="cdf9e-110">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="cdf9e-111">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-111">Attributes and elements</span></span>

<span data-ttu-id="cdf9e-112">下列各節說明屬性、子項目和父元素：</span><span class="sxs-lookup"><span data-stu-id="cdf9e-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="cdf9e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cdf9e-113">Attributes</span></span>

|<span data-ttu-id="cdf9e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cdf9e-114">Attribute</span></span>|<span data-ttu-id="cdf9e-115">描述</span><span class="sxs-lookup"><span data-stu-id="cdf9e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdf9e-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="cdf9e-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="cdf9e-117">布林值，指定服務中所有作業是否都模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="cdf9e-118">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cdf9e-119">當特定服務作業模擬呼叫端時，執行緒內容會在執行指定的服務之前切換為呼叫端內容。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="cdf9e-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="cdf9e-120">principalPermissionMode</span></span>|<span data-ttu-id="cdf9e-121">設定用於在伺服器上執行作業的原則。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="cdf9e-122">包括下列值：</span><span class="sxs-lookup"><span data-stu-id="cdf9e-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="cdf9e-123">-無</span><span class="sxs-lookup"><span data-stu-id="cdf9e-123">-   None</span></span><br /><span data-ttu-id="cdf9e-124">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="cdf9e-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="cdf9e-125">-   UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="cdf9e-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="cdf9e-126">-Custom</span><span class="sxs-lookup"><span data-stu-id="cdf9e-126">-   Custom</span></span><br /><br /> <span data-ttu-id="cdf9e-127">預設值為 UseWindowsGroups。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="cdf9e-128">此值的型別為 <xref:System.ServiceModel.Description.PrincipalPermissionMode>。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="cdf9e-129">如需使用此屬性的詳細資訊，請參閱 [How to：使用 PrincipalPermissionAttribute 類別 @ no__t-0 來限制存取。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="cdf9e-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="cdf9e-130">roleProviderName</span></span>|<span data-ttu-id="cdf9e-131">字串，指定角色提供者的名稱，它會提供 Windows Communication Foundation (WCF) 應用程式的角色資訊。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="cdf9e-132">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="cdf9e-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="cdf9e-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="cdf9e-134">字串，其中包含服務授權管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="cdf9e-135">如需詳細資訊，請參閱<xref:System.ServiceModel.ServiceAuthorizationManager>。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="cdf9e-136">子元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-136">Child elements</span></span>

|<span data-ttu-id="cdf9e-137">元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-137">Element</span></span>|<span data-ttu-id="cdf9e-138">描述</span><span class="sxs-lookup"><span data-stu-id="cdf9e-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdf9e-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="cdf9e-139">authorizationPolicies</span></span>|<span data-ttu-id="cdf9e-140">包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="cdf9e-141">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="cdf9e-142">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="cdf9e-143">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="cdf9e-144">如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="cdf9e-145">父元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-145">Parent elements</span></span>

|<span data-ttu-id="cdf9e-146">元素</span><span class="sxs-lookup"><span data-stu-id="cdf9e-146">Element</span></span>|<span data-ttu-id="cdf9e-147">描述</span><span class="sxs-lookup"><span data-stu-id="cdf9e-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdf9e-148">\<behavior></span><span class="sxs-lookup"><span data-stu-id="cdf9e-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="cdf9e-149">包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="cdf9e-150">備註</span><span class="sxs-lookup"><span data-stu-id="cdf9e-150">Remarks</span></span>

<span data-ttu-id="cdf9e-151">本章節包含會影響授權的項目、自訂的角色提供者，以及模擬。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="cdf9e-152">`principalPermissionMode` 屬性會指定要在授權使用保護的方法時使用的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="cdf9e-153">預設值為 `UseWindowsGroups`，其指定了在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="cdf9e-154">您也可以指定 `UseAspNetRoles`，以使用在 \<system. web > 元素下設定的自訂角色提供者，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cdf9e-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="cdf9e-155">下列程式碼顯示搭配 `principalPermissionMode` 屬性使用的 `roleProviderName`：</span><span class="sxs-lookup"><span data-stu-id="cdf9e-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="cdf9e-156">如需使用此 configuration 元素的詳細範例，請參閱[授權存取服務作業](../../../wcf/samples/authorizing-access-to-service-operations.md)和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cdf9e-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf9e-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="cdf9e-158">安全性行為</span><span class="sxs-lookup"><span data-stu-id="cdf9e-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cdf9e-159">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="cdf9e-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- <span data-ttu-id="cdf9e-160">[如何：為服務建立自訂授權管理員 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="cdf9e-160">[How to: Create a Custom Authorization Manager for a Service](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)</span></span>
- <span data-ttu-id="cdf9e-161">[如何：使用 PrincipalPermissionAttribute 類別來限制存取 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="cdf9e-161">[How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)</span></span>
- [<span data-ttu-id="cdf9e-162">授權原則</span><span class="sxs-lookup"><span data-stu-id="cdf9e-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
