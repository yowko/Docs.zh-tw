---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: a1fcc59550904a34eced8e87fa9bc54a334acd03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937166"
---
# <a name="servicesecurityaudit"></a><span data-ttu-id="33b1b-101">\<serviceSecurityAudit></span><span class="sxs-lookup"><span data-stu-id="33b1b-101">\<serviceSecurityAudit></span></span>
<span data-ttu-id="33b1b-102">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="33b1b-102">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
 <span data-ttu-id="33b1b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="33b1b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="33b1b-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="33b1b-104">\<behaviors></span></span>  
<span data-ttu-id="33b1b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="33b1b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="33b1b-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="33b1b-106">\<behavior></span></span>  
<span data-ttu-id="33b1b-107">\<serviceSecurityAudit></span><span class="sxs-lookup"><span data-stu-id="33b1b-107">\<serviceSecurityAudit></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b1b-108">語法</span><span class="sxs-lookup"><span data-stu-id="33b1b-108">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33b1b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="33b1b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="33b1b-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="33b1b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33b1b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="33b1b-111">Attributes</span></span>  
  
|<span data-ttu-id="33b1b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="33b1b-112">Attribute</span></span>|<span data-ttu-id="33b1b-113">說明</span><span class="sxs-lookup"><span data-stu-id="33b1b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33b1b-114">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="33b1b-114">auditLogLocation</span></span>|<span data-ttu-id="33b1b-115">指定稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="33b1b-115">Specifies the location of the audit log.</span></span> <span data-ttu-id="33b1b-116">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="33b1b-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="33b1b-117">預設安全性事件會寫入 Windows XP 上的應用程式記錄檔, 以及 Windows Server 2003 和 Windows Vista 上的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33b1b-117">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="33b1b-118">應用程式Audit 事件會寫入至應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33b1b-118">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="33b1b-119">安全級Audit 事件會寫入至安全性事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33b1b-119">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="33b1b-120">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="33b1b-120">The default value is Default.</span></span> <span data-ttu-id="33b1b-121">如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLogLocation>。</span><span class="sxs-lookup"><span data-stu-id="33b1b-121">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="33b1b-122">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="33b1b-122">suppressAuditFailure</span></span>|<span data-ttu-id="33b1b-123">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="33b1b-123">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="33b1b-124">應用程式應會收到稽核記錄檔寫入失敗的通知。</span><span class="sxs-lookup"><span data-stu-id="33b1b-124">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="33b1b-125">如果您的應用程式不是設計用來處理稽核失敗，應使用這個屬性來隱藏稽核記錄檔的寫入失敗。</span><span class="sxs-lookup"><span data-stu-id="33b1b-125">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="33b1b-126">如果這個屬性是 `true`，則 OutOfMemoryException、StackOverFlowException、ThreadAbortException 和 ArgumentException 以外的例外狀況會由系統處理，而不會傳播至應用程式；這些例外狀況是因為嘗試寫入稽核事件所造成的。</span><span class="sxs-lookup"><span data-stu-id="33b1b-126">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="33b1b-127">如果這個屬性是 `false`，則所有因嘗試寫入稽核事件而造成的例外狀況都會向上傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="33b1b-127">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="33b1b-128">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="33b1b-128">The default is `true`.</span></span>|  
|<span data-ttu-id="33b1b-129">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="33b1b-129">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="33b1b-130">指定記錄在稽核記錄檔中的授權事件類型。</span><span class="sxs-lookup"><span data-stu-id="33b1b-130">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="33b1b-131">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="33b1b-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="33b1b-132">無不會執行任何服務授權事件的審核。</span><span class="sxs-lookup"><span data-stu-id="33b1b-132">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="33b1b-133">Success只會審核成功的服務授權事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-133">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="33b1b-134">出只會審核失敗的服務授權事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-134">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="33b1b-135">- SuccessOrFailure:成功和失敗的服務授權事件都會進行審核。</span><span class="sxs-lookup"><span data-stu-id="33b1b-135">-   SuccessOrFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="33b1b-136">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="33b1b-136">The default value is None.</span></span> <span data-ttu-id="33b1b-137">如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="33b1b-137">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="33b1b-138">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="33b1b-138">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="33b1b-139">指定稽核事件記錄的訊息驗證類型。</span><span class="sxs-lookup"><span data-stu-id="33b1b-139">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="33b1b-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="33b1b-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="33b1b-141">無不會產生任何 audit 事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-141">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="33b1b-142">Success只會記錄成功的安全性 (包括訊息簽章驗證、加密和權杖驗證的完整驗證) 事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-142">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="33b1b-143">出只會記錄失敗的事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-143">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="33b1b-144">- SuccessOrFailure:成功和失敗事件都會記錄下來。</span><span class="sxs-lookup"><span data-stu-id="33b1b-144">-   SuccessOrFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="33b1b-145">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="33b1b-145">The default value is None.</span></span> <span data-ttu-id="33b1b-146">如需詳細資訊，請參閱 <xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="33b1b-146">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33b1b-147">子元素</span><span class="sxs-lookup"><span data-stu-id="33b1b-147">Child Elements</span></span>  
 <span data-ttu-id="33b1b-148">無。</span><span class="sxs-lookup"><span data-stu-id="33b1b-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33b1b-149">父項目</span><span class="sxs-lookup"><span data-stu-id="33b1b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="33b1b-150">項目</span><span class="sxs-lookup"><span data-stu-id="33b1b-150">Element</span></span>|<span data-ttu-id="33b1b-151">說明</span><span class="sxs-lookup"><span data-stu-id="33b1b-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33b1b-152">\<behavior></span><span class="sxs-lookup"><span data-stu-id="33b1b-152">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="33b1b-153">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="33b1b-153">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33b1b-154">備註</span><span class="sxs-lookup"><span data-stu-id="33b1b-154">Remarks</span></span>  
 <span data-ttu-id="33b1b-155">此設定元素用來審查 Windows Communication Foundation (WCF) 驗證事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-155">This configuration element is used to audit Windows Communication Foundation (WCF) authentication events.</span></span> <span data-ttu-id="33b1b-156">啟用稽核時，可以稽核成功或失敗的驗證嘗試 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="33b1b-156">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="33b1b-157">事件會寫入三個事件記錄檔之一：應用程式、安全性或作業系統版本的預設記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33b1b-157">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="33b1b-158">使用 Windows 事件檢視器，即可檢視所有的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="33b1b-158">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="33b1b-159">如需使用此設定元素的詳細範例, 請參閱[服務的審核行為](../../../wcf/samples/service-auditing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="33b1b-159">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="33b1b-160">根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。</span><span class="sxs-lookup"><span data-stu-id="33b1b-160">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="33b1b-161">將 `auditLogLocation` 屬性設定為 'Application' 或 'Security'，即可指定稽核事件的位置。</span><span class="sxs-lookup"><span data-stu-id="33b1b-161">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="33b1b-162">如需詳細資訊，請參閱[如何：Audit Security 事件](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="33b1b-162">For more information, see [How to: Audit Security Events](../../../wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="33b1b-163">如果事件是在安全性記錄檔中寫入, 則應該將 [LocalSecurityPolicy-> 啟用物件存取] 設定為 [成功] 和 [失敗]。</span><span class="sxs-lookup"><span data-stu-id="33b1b-163">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="33b1b-164">在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。</span><span class="sxs-lookup"><span data-stu-id="33b1b-164">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="33b1b-165">訊息驗證稽核記錄的分類為 "MessageAuthentication"，而服務驗證稽核記錄的分類則為 'ServiceAuthorization'。</span><span class="sxs-lookup"><span data-stu-id="33b1b-165">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="33b1b-166">訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。</span><span class="sxs-lookup"><span data-stu-id="33b1b-166">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="33b1b-167">這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。</span><span class="sxs-lookup"><span data-stu-id="33b1b-167">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="33b1b-168">服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。</span><span class="sxs-lookup"><span data-stu-id="33b1b-168">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="33b1b-169">它們會提供授權是否成功或失敗的相關資訊, 以及用戶端的身分識別、訊息傳送到的端點、與訊息相關聯的動作, 以及從內送訊息, 以及做出存取決策的授權管理員類型。</span><span class="sxs-lookup"><span data-stu-id="33b1b-169">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33b1b-170">範例</span><span class="sxs-lookup"><span data-stu-id="33b1b-170">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33b1b-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33b1b-171">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [<span data-ttu-id="33b1b-172">安全性行為</span><span class="sxs-lookup"><span data-stu-id="33b1b-172">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="33b1b-173">稽核</span><span class="sxs-lookup"><span data-stu-id="33b1b-173">Auditing</span></span>](../../../wcf/feature-details/auditing-security-events.md)
- [<span data-ttu-id="33b1b-174">如何：Audit Security 事件</span><span class="sxs-lookup"><span data-stu-id="33b1b-174">How to: Audit Security Events</span></span>](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [<span data-ttu-id="33b1b-175">服務稽核行為</span><span class="sxs-lookup"><span data-stu-id="33b1b-175">Service Auditing Behavior</span></span>](../../../wcf/samples/service-auditing-behavior.md)
