---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 25355acfd7bc82ccff33f68a690f3f02d1235438
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="ltservicesecurityauditgt"></a><span data-ttu-id="4fcc4-102">&lt;serviceSecurityAudit&gt;</span><span class="sxs-lookup"><span data-stu-id="4fcc4-102">&lt;serviceSecurityAudit&gt;</span></span>
<span data-ttu-id="4fcc4-103">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-103">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
 <span data-ttu-id="4fcc4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4fcc4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4fcc4-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4fcc4-105">\<behaviors></span></span>  
<span data-ttu-id="4fcc4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4fcc4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4fcc4-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4fcc4-107">\<behavior></span></span>  
<span data-ttu-id="4fcc4-108">\<serviceSecurityAudit></span><span class="sxs-lookup"><span data-stu-id="4fcc4-108">\<serviceSecurityAudit></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcc4-109">語法</span><span class="sxs-lookup"><span data-stu-id="4fcc4-109">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessOrFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fcc4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4fcc4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4fcc4-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fcc4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4fcc4-112">Attributes</span></span>  
  
|<span data-ttu-id="4fcc4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4fcc4-113">Attribute</span></span>|<span data-ttu-id="4fcc4-114">描述</span><span class="sxs-lookup"><span data-stu-id="4fcc4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fcc4-115">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="4fcc4-115">auditLogLocation</span></span>|<span data-ttu-id="4fcc4-116">指定稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-116">Specifies the location of the audit log.</span></span> <span data-ttu-id="4fcc4-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="4fcc4-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4fcc4-118">預設： 安全性事件會寫入應用程式記錄檔到事件記錄檔的 Windows XP 和 Windows Server 2003 和 Windows Vista 上。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-118">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="4fcc4-119">應用程式： 稽核事件會寫入應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-119">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="4fcc4-120">安全性： 稽核事件會寫入安全性記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-120">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="4fcc4-121">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-121">The default value is Default.</span></span> <span data-ttu-id="4fcc4-122">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLogLocation>。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-122">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="4fcc4-123">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="4fcc4-123">suppressAuditFailure</span></span>|<span data-ttu-id="4fcc4-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-124">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="4fcc4-125">應用程式應會收到稽核記錄檔寫入失敗的通知。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-125">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="4fcc4-126">如果您的應用程式不是設計用來處理稽核失敗，應使用這個屬性來隱藏稽核記錄檔的寫入失敗。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-126">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="4fcc4-127">如果這個屬性是 `true`，則 OutOfMemoryException、StackOverFlowException、ThreadAbortException 和 ArgumentException 以外的例外狀況會由系統處理，而不會傳播至應用程式；這些例外狀況是因為嘗試寫入稽核事件所造成的。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-127">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="4fcc4-128">如果這個屬性是 `false`，則所有因嘗試寫入稽核事件而造成的例外狀況都會向上傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-128">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="4fcc4-129">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-129">The default is `true`.</span></span>|  
|<span data-ttu-id="4fcc4-130">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4fcc4-130">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="4fcc4-131">指定記錄在稽核記錄檔中的授權事件類型。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-131">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="4fcc4-132">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="4fcc4-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4fcc4-133">-無： 服務授權事件的稽核不會執行。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-133">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="4fcc4-134">-Success： 只成功的服務授權稽核事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-134">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="4fcc4-135">失敗： 只失敗服務授權稽核事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-135">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="4fcc4-136">-SuccessOrFailure： 同時稽核成功和失敗的服務授權事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-136">-   SuccessOrFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="4fcc4-137">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-137">The default value is None.</span></span> <span data-ttu-id="4fcc4-138">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-138">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="4fcc4-139">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4fcc4-139">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="4fcc4-140">指定稽核事件記錄的訊息驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-140">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="4fcc4-141">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="4fcc4-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4fcc4-142">-無： 稽核會產生任何事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-142">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="4fcc4-143">-Success： 記錄成功的安全性 （完整驗證，包括訊息簽章驗證、 cipher 和權杖驗證） 事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-143">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="4fcc4-144">失敗： 只失敗記錄事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-144">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="4fcc4-145">-SuccessOrFailure： 同時記錄成功和失敗的事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-145">-   SuccessOrFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="4fcc4-146">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-146">The default value is None.</span></span> <span data-ttu-id="4fcc4-147">如需詳細資訊，請參閱<xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-147">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fcc4-148">子元素</span><span class="sxs-lookup"><span data-stu-id="4fcc4-148">Child Elements</span></span>  
 <span data-ttu-id="4fcc4-149">無。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fcc4-150">父項目</span><span class="sxs-lookup"><span data-stu-id="4fcc4-150">Parent Elements</span></span>  
  
|<span data-ttu-id="4fcc4-151">項目</span><span class="sxs-lookup"><span data-stu-id="4fcc4-151">Element</span></span>|<span data-ttu-id="4fcc4-152">描述</span><span class="sxs-lookup"><span data-stu-id="4fcc4-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fcc4-153">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4fcc4-153">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4fcc4-154">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-154">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fcc4-155">備註</span><span class="sxs-lookup"><span data-stu-id="4fcc4-155">Remarks</span></span>  
 <span data-ttu-id="4fcc4-156">這個組態項目會用來稽核 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 驗證事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-156">This configuraton element is used to audit [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] authentication events.</span></span> <span data-ttu-id="4fcc4-157">啟用稽核時，可以稽核成功或失敗的驗證嘗試 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-157">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="4fcc4-158">事件會寫入三個事件記錄檔之一：應用程式、安全性或作業系統版本的預設記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-158">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="4fcc4-159">使用 Windows 事件檢視器，即可檢視所有的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-159">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="4fcc4-160">使用這個組態項目詳細範例，請參閱[服務稽核行為](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-160">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="4fcc4-161">根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-161">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="4fcc4-162">將 `auditLogLocation` 屬性設定為 'Application' 或 'Security'，即可指定稽核事件的位置。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-162">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="4fcc4-163">如需詳細資訊，請參閱[How to： 稽核安全性事件](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-163">For more information, see [How to: Audit Security Events](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="4fcc4-164">如果事件要寫入安全性記錄檔，則 LocalSecurityPolicy-> Enable Object Access 應設為 "Success" 和 "Failure"。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-164">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="4fcc4-165">在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-165">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="4fcc4-166">訊息驗證稽核記錄的分類為 "MessageAuthentication"，而服務驗證稽核記錄的分類則為 'ServiceAuthorization'。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-166">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="4fcc4-167">訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-167">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="4fcc4-168">這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-168">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="4fcc4-169">服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-169">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="4fcc4-170">它們提供的資訊關於授權是否成功或失敗、 以及用戶端的身分識別，端點的訊息已傳送訊息時，所產生的授權內容的識別項相關聯的動作內送訊息，以及做出存取決策的授權管理員類型。</span><span class="sxs-lookup"><span data-stu-id="4fcc4-170">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fcc4-171">範例</span><span class="sxs-lookup"><span data-stu-id="4fcc4-171">Example</span></span>  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fcc4-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="4fcc4-172">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [<span data-ttu-id="4fcc4-173">安全性行為</span><span class="sxs-lookup"><span data-stu-id="4fcc4-173">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4fcc4-174">稽核</span><span class="sxs-lookup"><span data-stu-id="4fcc4-174">Auditing</span></span>](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="4fcc4-175">如何：稽核安全性事件</span><span class="sxs-lookup"><span data-stu-id="4fcc4-175">How to: Audit Security Events</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [<span data-ttu-id="4fcc4-176">服務稽核行為</span><span class="sxs-lookup"><span data-stu-id="4fcc4-176">Service Auditing Behavior</span></span>](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
