---
title: 服務稽核行為
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: ae7ed2059b491a71de9c806e78f1fb784da197fa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262563"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="84699-102">服務稽核行為</span><span class="sxs-lookup"><span data-stu-id="84699-102">Service Auditing Behavior</span></span>

<span data-ttu-id="84699-103">這個範例會示範如何使用 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 以啟用稽核服務作業期間的安全性事件。</span><span class="sxs-lookup"><span data-stu-id="84699-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="84699-104">這個範例是以 [消費者入門](getting-started-sample.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="84699-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="84699-105">服務和用戶端已使用進行設定 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="84699-105">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="84699-106">的 `mode` 屬性已 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 設定為 `Message` ，且已 `clientCredentialType` 設定為 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="84699-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="84699-107">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="84699-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84699-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="84699-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="84699-109">服務組態檔會使用 `serviceSecurityAudit` 項目設定稽核。</span><span class="sxs-lookup"><span data-stu-id="84699-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="84699-110">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="84699-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="84699-111">在主控台視窗中按 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="84699-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="84699-112">執行事件檢視器可看到結果稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="84699-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="84699-113">根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，而在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。</span><span class="sxs-lookup"><span data-stu-id="84699-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="84699-114">在 Windows Server 2008 和 Windows 7 上，您可以在應用程式記錄檔和服務記錄檔中查看稽核事件。</span><span class="sxs-lookup"><span data-stu-id="84699-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="84699-115">您可以藉由將屬性設定為「應用程式」或「安全性」來指定 audit 事件的位置 `auditLogLocation` 。</span><span class="sxs-lookup"><span data-stu-id="84699-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="84699-116">如需詳細資訊，請參閱 how [to： Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="84699-116">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="84699-117">如果事件是寫入安全性記錄檔中，則必須針對「成功」和「失敗」設定 LocalSecurityPolicy > 啟用物件存取。</span><span class="sxs-lookup"><span data-stu-id="84699-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="84699-118">在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。</span><span class="sxs-lookup"><span data-stu-id="84699-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="84699-119">訊息驗證審核記錄的分類為 "MessageAuthentication"，而服務授權審核記錄的分類為 "ServiceAuthorization"。</span><span class="sxs-lookup"><span data-stu-id="84699-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="84699-120">訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。</span><span class="sxs-lookup"><span data-stu-id="84699-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="84699-121">這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。</span><span class="sxs-lookup"><span data-stu-id="84699-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="84699-122">服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。</span><span class="sxs-lookup"><span data-stu-id="84699-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="84699-123">這些事件提供的訊息是關於授權是否成功或失敗以及用戶端的身分識别、訊息傳送的目的端點、與訊息相關聯的動作、由傳入訊息產生的授權內容識別碼，以及做出存取決策的授權管理員類型。</span><span class="sxs-lookup"><span data-stu-id="84699-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84699-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="84699-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="84699-125">確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="84699-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="84699-126">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="84699-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="84699-127">若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="84699-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84699-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84699-128">See also</span></span>

- [<span data-ttu-id="84699-129">稽核</span><span class="sxs-lookup"><span data-stu-id="84699-129">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="84699-130">作法：稽核安全性事件</span><span class="sxs-lookup"><span data-stu-id="84699-130">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)
