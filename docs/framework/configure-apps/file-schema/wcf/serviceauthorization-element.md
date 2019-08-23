---
title: <serviceAuthorization> 項目
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936408"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="563ed-102">\<serviceAuthorization > 元素</span><span class="sxs-lookup"><span data-stu-id="563ed-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="563ed-103">指定設定，這些設定會將存取權授權給服務作業。</span><span class="sxs-lookup"><span data-stu-id="563ed-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="563ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="563ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="563ed-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="563ed-105">\<behaviors></span></span>  
<span data-ttu-id="563ed-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="563ed-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="563ed-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="563ed-107">\<behavior></span></span>  
<span data-ttu-id="563ed-108">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="563ed-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="563ed-109">語法</span><span class="sxs-lookup"><span data-stu-id="563ed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="563ed-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="563ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="563ed-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="563ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="563ed-112">屬性</span><span class="sxs-lookup"><span data-stu-id="563ed-112">Attributes</span></span>  
  
|<span data-ttu-id="563ed-113">屬性</span><span class="sxs-lookup"><span data-stu-id="563ed-113">Attribute</span></span>|<span data-ttu-id="563ed-114">描述</span><span class="sxs-lookup"><span data-stu-id="563ed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="563ed-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="563ed-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="563ed-116">布林值，指定服務中所有作業是否都模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="563ed-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="563ed-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="563ed-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="563ed-118">當特定服務作業模擬呼叫端時，執行緒內容會在執行指定的服務之前切換為呼叫端內容。</span><span class="sxs-lookup"><span data-stu-id="563ed-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="563ed-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="563ed-119">principalPermissionMode</span></span>|<span data-ttu-id="563ed-120">設定用於在伺服器上執行作業的原則。</span><span class="sxs-lookup"><span data-stu-id="563ed-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="563ed-121">包括下列值：</span><span class="sxs-lookup"><span data-stu-id="563ed-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="563ed-122">-無</span><span class="sxs-lookup"><span data-stu-id="563ed-122">-   None</span></span><br /><span data-ttu-id="563ed-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="563ed-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="563ed-124">-   UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="563ed-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="563ed-125">-Custom</span><span class="sxs-lookup"><span data-stu-id="563ed-125">-   Custom</span></span><br /><br /> <span data-ttu-id="563ed-126">預設值為 UseWindowsGroups。</span><span class="sxs-lookup"><span data-stu-id="563ed-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="563ed-127">此值的型別為 <xref:System.ServiceModel.Description.PrincipalPermissionMode>。</span><span class="sxs-lookup"><span data-stu-id="563ed-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="563ed-128">如需使用此屬性的詳細資訊, [請參閱如何:使用 PrincipalPermissionAttribute 類別](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)來限制存取。</span><span class="sxs-lookup"><span data-stu-id="563ed-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="563ed-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="563ed-129">roleProviderName</span></span>|<span data-ttu-id="563ed-130">字串，指定角色提供者的名稱，它會提供 Windows Communication Foundation (WCF) 應用程式的角色資訊。</span><span class="sxs-lookup"><span data-stu-id="563ed-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="563ed-131">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="563ed-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="563ed-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="563ed-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="563ed-133">字串，其中包含服務授權管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="563ed-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="563ed-134">如需詳細資訊，請參閱 <xref:System.ServiceModel.ServiceAuthorizationManager>。</span><span class="sxs-lookup"><span data-stu-id="563ed-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="563ed-135">子元素</span><span class="sxs-lookup"><span data-stu-id="563ed-135">Child Elements</span></span>  
  
|<span data-ttu-id="563ed-136">項目</span><span class="sxs-lookup"><span data-stu-id="563ed-136">Element</span></span>|<span data-ttu-id="563ed-137">描述</span><span class="sxs-lookup"><span data-stu-id="563ed-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="563ed-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="563ed-138">authorizationPolicies</span></span>|<span data-ttu-id="563ed-139">包含授權原則型別的集合，使用 `add` 關鍵字可加入這些型別。</span><span class="sxs-lookup"><span data-stu-id="563ed-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="563ed-140">每個授權原則包含一個必要的 `policyType` 屬性字串。</span><span class="sxs-lookup"><span data-stu-id="563ed-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="563ed-141">該屬性會指定授權原則，可讓一組輸入宣告轉換成另一組宣告。</span><span class="sxs-lookup"><span data-stu-id="563ed-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="563ed-142">它可以做為授與或拒絕存取控制 (Access Control) 的基礎。</span><span class="sxs-lookup"><span data-stu-id="563ed-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="563ed-143">如需詳細資訊，請參閱 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="563ed-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="563ed-144">父項目</span><span class="sxs-lookup"><span data-stu-id="563ed-144">Parent Elements</span></span>  
  
|<span data-ttu-id="563ed-145">項目</span><span class="sxs-lookup"><span data-stu-id="563ed-145">Element</span></span>|<span data-ttu-id="563ed-146">描述</span><span class="sxs-lookup"><span data-stu-id="563ed-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="563ed-147">\<behavior></span><span class="sxs-lookup"><span data-stu-id="563ed-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="563ed-148">包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="563ed-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="563ed-149">備註</span><span class="sxs-lookup"><span data-stu-id="563ed-149">Remarks</span></span>  
 <span data-ttu-id="563ed-150">本章節包含會影響授權的項目、自訂的角色提供者，以及模擬。</span><span class="sxs-lookup"><span data-stu-id="563ed-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="563ed-151">`principalPermissionMode` 屬性會指定要在授權使用保護的方法時使用的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="563ed-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="563ed-152">預設值為 `UseWindowsGroups`，其指定了在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。</span><span class="sxs-lookup"><span data-stu-id="563ed-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="563ed-153">您也可以指定`UseAspNetRoles`使用\<在 system.web > 專案底下設定的自訂角色提供者, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="563ed-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="563ed-154">下列程式碼示範搭配 `roleProviderName` 屬性使用的 `principalPermissionMode`。</span><span class="sxs-lookup"><span data-stu-id="563ed-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="563ed-155">如需使用此 configuration 元素的詳細範例, 請參閱[授權存取服務作業](../../../wcf/samples/authorizing-access-to-service-operations.md)和[授權原則](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="563ed-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563ed-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="563ed-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="563ed-157">安全性行為</span><span class="sxs-lookup"><span data-stu-id="563ed-157">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="563ed-158">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="563ed-158">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="563ed-159">如何：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="563ed-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="563ed-160">如何：使用 PrincipalPermissionAttribute 類別來限制存取</span><span class="sxs-lookup"><span data-stu-id="563ed-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="563ed-161">授權原則</span><span class="sxs-lookup"><span data-stu-id="563ed-161">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
