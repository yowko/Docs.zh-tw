---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 6cec3373dae3127f16bb8a418a91a684554f2b0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153660"
---
# \<serviceSecurityAudit>

<span data-ttu-id="f38fe-101">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="f38fe-101">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceSecurityAudit>**  
  
## <a name="syntax"></a><span data-ttu-id="f38fe-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f38fe-102">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f38fe-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f38fe-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f38fe-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f38fe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f38fe-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f38fe-105">Attributes</span></span>  
  
|<span data-ttu-id="f38fe-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f38fe-106">Attribute</span></span>|<span data-ttu-id="f38fe-107">描述</span><span class="sxs-lookup"><span data-stu-id="f38fe-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f38fe-108">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="f38fe-108">auditLogLocation</span></span>|<span data-ttu-id="f38fe-109">指定稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="f38fe-109">Specifies the location of the audit log.</span></span> <span data-ttu-id="f38fe-110">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="f38fe-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f38fe-111">-Default：安全性事件會寫入 Windows XP 上的應用程式記錄檔，以及 Windows Server 2003 和 Windows Vista 上的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f38fe-111">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="f38fe-112">-Application： Audit 事件會寫入至應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f38fe-112">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="f38fe-113">-Security： Audit 事件會寫入安全性事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="f38fe-113">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="f38fe-114">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="f38fe-114">The default value is Default.</span></span> <span data-ttu-id="f38fe-115">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLogLocation>。</span><span class="sxs-lookup"><span data-stu-id="f38fe-115">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="f38fe-116">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="f38fe-116">suppressAuditFailure</span></span>|<span data-ttu-id="f38fe-117">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="f38fe-117">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="f38fe-118">應用程式應會收到稽核記錄檔寫入失敗的通知。</span><span class="sxs-lookup"><span data-stu-id="f38fe-118">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="f38fe-119">如果您的應用程式不是設計用來處理稽核失敗，應使用這個屬性來隱藏稽核記錄檔的寫入失敗。</span><span class="sxs-lookup"><span data-stu-id="f38fe-119">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="f38fe-120">如果這個屬性是 `true`，則 OutOfMemoryException、StackOverFlowException、ThreadAbortException 和 ArgumentException 以外的例外狀況會由系統處理，而不會傳播至應用程式；這些例外狀況是因為嘗試寫入稽核事件所造成的。</span><span class="sxs-lookup"><span data-stu-id="f38fe-120">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="f38fe-121">如果這個屬性是 `false`，則所有因嘗試寫入稽核事件而造成的例外狀況都會向上傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="f38fe-121">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="f38fe-122">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f38fe-122">The default is `true`.</span></span>|  
|<span data-ttu-id="f38fe-123">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="f38fe-123">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="f38fe-124">指定記錄在稽核記錄檔中的授權事件類型。</span><span class="sxs-lookup"><span data-stu-id="f38fe-124">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="f38fe-125">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="f38fe-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f38fe-126">-None：未執行任何服務授權事件的審核。</span><span class="sxs-lookup"><span data-stu-id="f38fe-126">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="f38fe-127">-Success：只會審核成功的服務授權事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-127">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="f38fe-128">-失敗：只會審核失敗的服務授權事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-128">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="f38fe-129">-SuccessOrFailure：成功和失敗的服務授權事件都會進行審核。</span><span class="sxs-lookup"><span data-stu-id="f38fe-129">-   SuccessOrFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="f38fe-130">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="f38fe-130">The default value is None.</span></span> <span data-ttu-id="f38fe-131">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="f38fe-131">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="f38fe-132">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="f38fe-132">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="f38fe-133">指定稽核事件記錄的訊息驗證類型。</span><span class="sxs-lookup"><span data-stu-id="f38fe-133">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="f38fe-134">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="f38fe-134">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f38fe-135">-None：不產生任何 audit 事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-135">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="f38fe-136">-Success：只會記錄成功的安全性 (完整驗證，包括訊息簽章驗證、密碼和權杖驗證) 事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-136">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="f38fe-137">-失敗：只會記錄失敗事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-137">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="f38fe-138">-SuccessOrFailure：記錄成功和失敗事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-138">-   SuccessOrFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="f38fe-139">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="f38fe-139">The default value is None.</span></span> <span data-ttu-id="f38fe-140">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="f38fe-140">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f38fe-141">子元素</span><span class="sxs-lookup"><span data-stu-id="f38fe-141">Child Elements</span></span>  

 <span data-ttu-id="f38fe-142">無。</span><span class="sxs-lookup"><span data-stu-id="f38fe-142">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f38fe-143">父項目</span><span class="sxs-lookup"><span data-stu-id="f38fe-143">Parent Elements</span></span>  
  
|<span data-ttu-id="f38fe-144">項目</span><span class="sxs-lookup"><span data-stu-id="f38fe-144">Element</span></span>|<span data-ttu-id="f38fe-145">描述</span><span class="sxs-lookup"><span data-stu-id="f38fe-145">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f38fe-146">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="f38fe-146">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f38fe-147">備註</span><span class="sxs-lookup"><span data-stu-id="f38fe-147">Remarks</span></span>  

 <span data-ttu-id="f38fe-148">這個設定元素用來 Windows Communication Foundation (WCF) 驗證事件來進行審核。</span><span class="sxs-lookup"><span data-stu-id="f38fe-148">This configuration element is used to audit Windows Communication Foundation (WCF) authentication events.</span></span> <span data-ttu-id="f38fe-149">啟用稽核時，可以稽核成功或失敗的驗證嘗試 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="f38fe-149">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="f38fe-150">事件會寫入三個事件記錄檔之一：應用程式、安全性或作業系統版本的預設記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f38fe-150">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="f38fe-151">使用 Windows 事件檢視器，即可檢視所有的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="f38fe-151">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="f38fe-152">如需使用此設定元素的詳細範例，請參閱 [服務審核行為](../../../wcf/samples/service-auditing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="f38fe-152">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="f38fe-153">根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。</span><span class="sxs-lookup"><span data-stu-id="f38fe-153">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="f38fe-154">將 `auditLogLocation` 屬性設定為 'Application' 或 'Security'，即可指定稽核事件的位置。</span><span class="sxs-lookup"><span data-stu-id="f38fe-154">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="f38fe-155">如需詳細資訊，請參閱 how [to： Audit Security Events](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="f38fe-155">For more information, see [How to: Audit Security Events](../../../wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="f38fe-156">如果事件是寫入安全性記錄檔中，則應該針對「成功」和「失敗」設定 LocalSecurityPolicy > 啟用物件存取。</span><span class="sxs-lookup"><span data-stu-id="f38fe-156">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="f38fe-157">在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。</span><span class="sxs-lookup"><span data-stu-id="f38fe-157">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="f38fe-158">訊息驗證稽核記錄的分類為 "MessageAuthentication"，而服務驗證稽核記錄的分類則為 'ServiceAuthorization'。</span><span class="sxs-lookup"><span data-stu-id="f38fe-158">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="f38fe-159">訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。</span><span class="sxs-lookup"><span data-stu-id="f38fe-159">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="f38fe-160">這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。</span><span class="sxs-lookup"><span data-stu-id="f38fe-160">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="f38fe-161">服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。</span><span class="sxs-lookup"><span data-stu-id="f38fe-161">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="f38fe-162">它們提供授權成功或失敗的相關資訊，以及用戶端的身分識別、訊息傳送至的端點、與訊息相關聯的動作、由傳入訊息產生的授權內容識別碼，以及做出存取決策的授權管理員類型。</span><span class="sxs-lookup"><span data-stu-id="f38fe-162">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f38fe-163">範例</span><span class="sxs-lookup"><span data-stu-id="f38fe-163">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f38fe-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38fe-164">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [<span data-ttu-id="f38fe-165">安全性行為</span><span class="sxs-lookup"><span data-stu-id="f38fe-165">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f38fe-166">稽核</span><span class="sxs-lookup"><span data-stu-id="f38fe-166">Auditing</span></span>](../../../wcf/feature-details/auditing-security-events.md)
- [<span data-ttu-id="f38fe-167">作法：稽核安全性事件</span><span class="sxs-lookup"><span data-stu-id="f38fe-167">How to: Audit Security Events</span></span>](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [<span data-ttu-id="f38fe-168">服務稽核行為</span><span class="sxs-lookup"><span data-stu-id="f38fe-168">Service Auditing Behavior</span></span>](../../../wcf/samples/service-auditing-behavior.md)
