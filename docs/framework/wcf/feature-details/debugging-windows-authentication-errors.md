---
title: 偵錯 Windows 驗證錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: 28c70ca860083808c93fa58b498e22ea4e4ca6cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299445"
---
# <a name="debugging-windows-authentication-errors"></a><span data-ttu-id="1963e-102">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="1963e-102">Debugging Windows Authentication Errors</span></span>
<span data-ttu-id="1963e-103">當使用 Windows 驗證做為安全性機制時，安全性支援提供者介面 (SSPI) 便會處理安全性程序。</span><span class="sxs-lookup"><span data-stu-id="1963e-103">When using Windows authentication as a security mechanism, the Security Support Provider Interface (SSPI) handles security processes.</span></span> <span data-ttu-id="1963e-104">當安全性錯誤發生在 SSPI 層時，它們會顯示由 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="1963e-104">When security errors occur at the SSPI layer, they are surfaced by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1963e-105">本主題會提供可協助診斷這些錯誤的架構與問題集。</span><span class="sxs-lookup"><span data-stu-id="1963e-105">This topic provides a framework and set of questions to help diagnose the errors.</span></span>  
  
 <span data-ttu-id="1963e-106">如需 Kerberos 通訊協定的概觀，請參閱 < [Kerberos 說明 >](https://go.microsoft.com/fwlink/?LinkID=86946); 如需 SSPI 的概觀，請參閱[SSPI](https://go.microsoft.com/fwlink/?LinkId=88941)。</span><span class="sxs-lookup"><span data-stu-id="1963e-106">For an overview of the Kerberos protocol, see [Kerberos Explained](https://go.microsoft.com/fwlink/?LinkID=86946); for an overview of SSPI, see [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).</span></span>  
  
 <span data-ttu-id="1963e-107">對於 Windows 驗證，WCF 通常會使用*交涉*安全性支援提供者 (SSP)，它會執行用戶端與服務之間的 Kerberos 相互驗證。</span><span class="sxs-lookup"><span data-stu-id="1963e-107">For Windows authentication, WCF typically uses the *Negotiate* Security Support Provider (SSP), which performs Kerberos mutual authentication between the client and service.</span></span> <span data-ttu-id="1963e-108">如果無法使用，WCF 會回復到 NT LAN Manager (NTLM) 的預設 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1963e-108">If the Kerberos protocol is not available, by default WCF falls back to NT LAN Manager (NTLM).</span></span> <span data-ttu-id="1963e-109">不過，您可以設定 WCF 只使用 Kerberos 通訊協定 （並擲回例外狀況，如果 Kerberos 無法使用）。</span><span class="sxs-lookup"><span data-stu-id="1963e-109">However, you can configure WCF to use only the Kerberos protocol (and to throw an exception if Kerberos is not available).</span></span> <span data-ttu-id="1963e-110">您也可以設定成使用限制的型態的 Kerberos 通訊協定的 WCF。</span><span class="sxs-lookup"><span data-stu-id="1963e-110">You can also configure WCF to use restricted forms of the Kerberos protocol.</span></span>  
  
## <a name="debugging-methodology"></a><span data-ttu-id="1963e-111">偵錯方法</span><span class="sxs-lookup"><span data-stu-id="1963e-111">Debugging Methodology</span></span>  
 <span data-ttu-id="1963e-112">下面列出基本的方法：</span><span class="sxs-lookup"><span data-stu-id="1963e-112">The basic method is as follows:</span></span>  
  
1. <span data-ttu-id="1963e-113">判斷您是否在使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="1963e-113">Determine whether you are using Windows authentication.</span></span> <span data-ttu-id="1963e-114">如果您是使用其他任何配置，這個主題就不適用。</span><span class="sxs-lookup"><span data-stu-id="1963e-114">If you are using any other scheme, this topic does not apply.</span></span>  
  
2. <span data-ttu-id="1963e-115">如果您不確定您使用 Windows 驗證，判斷您的 WCF 組態是否使用 Kerberos direct 或 Negotiate。</span><span class="sxs-lookup"><span data-stu-id="1963e-115">If you are sure you are using Windows authentication, determine whether your WCF configuration uses Kerberos direct or Negotiate.</span></span>  
  
3. <span data-ttu-id="1963e-116">判斷出您的組態是使用 Kerberos 通訊協定或 NTLM 之後，您就能夠了解在正確環境中的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1963e-116">Once you have determined whether your configuration is using the Kerberos protocol or NTLM, you can understand error messages in the correct context.</span></span>  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a><span data-ttu-id="1963e-117">Kerberos 通訊協定與 NTLM 的可用性</span><span class="sxs-lookup"><span data-stu-id="1963e-117">Availability of the Kerberos Protocol and NTLM</span></span>  
 <span data-ttu-id="1963e-118">Kerberos SSP 需要網域控制站擔任 Kerberos 金鑰發佈中心 (KDC)。</span><span class="sxs-lookup"><span data-stu-id="1963e-118">The Kerberos SSP requires a domain controller to act as the Kerberos Key Distribution Center (KDC).</span></span> <span data-ttu-id="1963e-119">唯有當用戶端與服務都使用網域識別時，才可以使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1963e-119">The Kerberos protocol is available only when both the client and service are using domain identities.</span></span> <span data-ttu-id="1963e-120">在其他帳戶組合中則是使用 NTLM，如下表摘要所示。</span><span class="sxs-lookup"><span data-stu-id="1963e-120">In other account combinations, NTLM is used, as summarized in the following table.</span></span>  
  
 <span data-ttu-id="1963e-121">表格標頭會顯示伺服器可能使用的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="1963e-121">The table headers show possible account types used by the server.</span></span> <span data-ttu-id="1963e-122">左欄則顯示用戶端可能使用的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="1963e-122">The left column shows possible account types used by the client.</span></span>  
  
||<span data-ttu-id="1963e-123">本機使用者</span><span class="sxs-lookup"><span data-stu-id="1963e-123">Local User</span></span>|<span data-ttu-id="1963e-124">本機系統</span><span class="sxs-lookup"><span data-stu-id="1963e-124">Local System</span></span>|<span data-ttu-id="1963e-125">網域使用者</span><span class="sxs-lookup"><span data-stu-id="1963e-125">Domain User</span></span>|<span data-ttu-id="1963e-126">網域電腦</span><span class="sxs-lookup"><span data-stu-id="1963e-126">Domain Machine</span></span>|  
|-|----------------|------------------|-----------------|--------------------|  
|<span data-ttu-id="1963e-127">本機使用者</span><span class="sxs-lookup"><span data-stu-id="1963e-127">Local User</span></span>|<span data-ttu-id="1963e-128">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-128">NTLM</span></span>|<span data-ttu-id="1963e-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-129">NTLM</span></span>|<span data-ttu-id="1963e-130">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-130">NTLM</span></span>|<span data-ttu-id="1963e-131">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-131">NTLM</span></span>|  
|<span data-ttu-id="1963e-132">本機系統</span><span class="sxs-lookup"><span data-stu-id="1963e-132">Local System</span></span>|<span data-ttu-id="1963e-133">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-133">Anonymous NTLM</span></span>|<span data-ttu-id="1963e-134">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-134">Anonymous NTLM</span></span>|<span data-ttu-id="1963e-135">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-135">Anonymous NTLM</span></span>|<span data-ttu-id="1963e-136">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-136">Anonymous NTLM</span></span>|  
|<span data-ttu-id="1963e-137">網域使用者</span><span class="sxs-lookup"><span data-stu-id="1963e-137">Domain User</span></span>|<span data-ttu-id="1963e-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-138">NTLM</span></span>|<span data-ttu-id="1963e-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-139">NTLM</span></span>|<span data-ttu-id="1963e-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1963e-140">Kerberos</span></span>|<span data-ttu-id="1963e-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1963e-141">Kerberos</span></span>|  
|<span data-ttu-id="1963e-142">網域電腦</span><span class="sxs-lookup"><span data-stu-id="1963e-142">Domain Machine</span></span>|<span data-ttu-id="1963e-143">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-143">NTLM</span></span>|<span data-ttu-id="1963e-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="1963e-144">NTLM</span></span>|<span data-ttu-id="1963e-145">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1963e-145">Kerberos</span></span>|<span data-ttu-id="1963e-146">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1963e-146">Kerberos</span></span>|  
  
 <span data-ttu-id="1963e-147">具體而言，這四種帳戶類型包括：</span><span class="sxs-lookup"><span data-stu-id="1963e-147">Specifically, the four account types include:</span></span>  
  
-   <span data-ttu-id="1963e-148">本機使用者：僅限電腦的使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="1963e-148">Local User: Machine-only user profile.</span></span> <span data-ttu-id="1963e-149">例如：`MachineName\Administrator` 或 `MachineName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="1963e-149">For example: `MachineName\Administrator` or `MachineName\ProfileName`.</span></span>  
  
-   <span data-ttu-id="1963e-150">本機系統：內建帳戶 SYSTEM 未加入網域的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1963e-150">Local System: The built-in account SYSTEM on a machine that is not joined to a domain.</span></span>  
  
-   <span data-ttu-id="1963e-151">網域使用者：在 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1963e-151">Domain User: A user account on a Windows domain.</span></span> <span data-ttu-id="1963e-152">例如：`DomainName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="1963e-152">For example: `DomainName\ProfileName`.</span></span>  
  
-   <span data-ttu-id="1963e-153">網域電腦：加入 Windows 網域的機器上執行的機器身分識別與處理程序。</span><span class="sxs-lookup"><span data-stu-id="1963e-153">Domain Machine: A process with machine identity running on a machine joined to a Windows domain.</span></span> <span data-ttu-id="1963e-154">例如：`MachineName\Network Service`。</span><span class="sxs-lookup"><span data-stu-id="1963e-154">For example: `MachineName\Network Service`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1963e-155">當呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 類別的 <xref:System.ServiceModel.ServiceHost> 方法時，便會擷取服務認證。</span><span class="sxs-lookup"><span data-stu-id="1963e-155">The service credential is captured when the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method of the <xref:System.ServiceModel.ServiceHost> class is called.</span></span> <span data-ttu-id="1963e-156">每當用戶端傳送訊息時就會讀取此用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="1963e-156">The client credential is read whenever the client sends a message.</span></span>  
  
## <a name="common-windows-authentication-problems"></a><span data-ttu-id="1963e-157">常見 Windows 驗證問題</span><span class="sxs-lookup"><span data-stu-id="1963e-157">Common Windows Authentication Problems</span></span>  
 <span data-ttu-id="1963e-158">本節會討論一些常見的 Windows 驗證問題以及可能的補救方法。</span><span class="sxs-lookup"><span data-stu-id="1963e-158">This section discusses some common Windows authentication problems and possible remedies.</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="1963e-159">Kerberos 通訊協定</span><span class="sxs-lookup"><span data-stu-id="1963e-159">Kerberos Protocol</span></span>  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a><span data-ttu-id="1963e-160">Kerberos 通訊協定的 SPN/UPN 問題</span><span class="sxs-lookup"><span data-stu-id="1963e-160">SPN/UPN Problems with the Kerberos Protocol</span></span>  
 <span data-ttu-id="1963e-161">當使用 Windows 驗證，而且 SSPI 有使用或交涉 Kerberos 通訊協定時，用戶端端點所使用的 URL 就必須包含在服務 URL 內之服務主機的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="1963e-161">When using Windows authentication, and the Kerberos protocol is used or negotiated by SSPI, the URL the client endpoint uses must include the fully qualified domain name of the service's host inside the service URL.</span></span> <span data-ttu-id="1963e-162">這是假設服務執行所在的帳戶具有將電腦加入 Active Directory 網域，其作法是最常執行服務時，會建立電腦 （預設） 服務主體名稱 (SPN) 金鑰的存取權網路服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="1963e-162">This assumes that the account under which the service is running has access to the machine (default) service principal name (SPN) key that is created when the computer is added to the Active Directory domain, which is most commonly done by running the service under the Network Service account.</span></span> <span data-ttu-id="1963e-163">如果服務無法存取電腦 SPN 金鑰，您就必須在用戶端端點身分識別中，提供用來執行服務之帳戶的正確 SPN 或使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="1963e-163">If the service does not have access to the machine SPN key, you must supply the correct SPN or user principal name (UPN) of the account under which the service is running in the client's endpoint identity.</span></span> <span data-ttu-id="1963e-164">如需 WCF 搭配 SPN 與 UPN 的運作方式的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="1963e-164">For more information about how WCF works with SPN and UPN, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="1963e-165">在負載平衡的使用案例 (例如 Web 伺服陣列與 Web 處理序區) 中，常見的作法是為每一個應用程式定義一個唯一的帳戶、指派一個 SPN 給該帳戶，並且確保應用程式的所有服務都以該帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="1963e-165">In load-balancing scenarios, such as Web farms or Web gardens, a common practice is to define a unique account for each application, assign an SPN to that account, and ensure that all of the application's services run in that account.</span></span>  
  
 <span data-ttu-id="1963e-166">如果您要取得服務帳戶的 SPN，您必須是 Active Directory 網域的管理員。</span><span class="sxs-lookup"><span data-stu-id="1963e-166">To obtain an SPN for your service's account, you need to be an Active Directory domain administrator.</span></span> <span data-ttu-id="1963e-167">如需詳細資訊，請參閱 < [Kerberos 技術補充的 Windows](https://go.microsoft.com/fwlink/?LinkID=88330)。</span><span class="sxs-lookup"><span data-stu-id="1963e-167">For more information, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkID=88330).</span></span>  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a><span data-ttu-id="1963e-168">Kerberos 通訊協定 Direct 要求使用網域電腦帳戶來執行服務。</span><span class="sxs-lookup"><span data-stu-id="1963e-168">Kerberos Protocol Direct Requires the Service to Run Under a Domain Machine Account</span></span>  
 <span data-ttu-id="1963e-169">當 `ClientCredentialType` 屬性設定為 `Windows`，而且 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性設定為 `false` 時，便會發生這種情況，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1963e-169">This occurs when the `ClientCredentialType` property is set to `Windows` and the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> property is set to `false`, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 <span data-ttu-id="1963e-170">若要修正此問題，請使用網域電腦帳戶來執行服務，例如，在加入網域之電腦上的 Network Service 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1963e-170">To remedy, run the service using a Domain Machine account, such as Network Service, on a domain joined machine.</span></span>  
  
### <a name="delegation-requires-credential-negotiation"></a><span data-ttu-id="1963e-171">委派需要認證交涉</span><span class="sxs-lookup"><span data-stu-id="1963e-171">Delegation Requires Credential Negotiation</span></span>  
 <span data-ttu-id="1963e-172">若要將 Kerberos 驗證通訊協定與委派搭配使用，您必須實作具有認證交涉的 Kerberos 通訊協定 (有時也稱做「多支線」(Multi-leg) 或「多步驟」(Multi-step) Kerberos)。</span><span class="sxs-lookup"><span data-stu-id="1963e-172">To use the Kerberos authentication protocol with delegation, you must implement the Kerberos protocol with credential negotiation (sometimes called "multi-leg" or "multi-step" Kerberos).</span></span> <span data-ttu-id="1963e-173">如果您實作不具有認證交涉的 Kerberos 驗證 (有時也稱做「單次」(One-shot) 或「單支線」(Single-leg) Kerberos)，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1963e-173">If you implement Kerberos authentication without credential negotiation (sometimes called "one-shot" or "single-leg" Kerberos), an exception will be thrown.</span></span>  
  
 <span data-ttu-id="1963e-174">若要實作具有認證交涉的 Kerberos，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1963e-174">To implement Kerberos with credential negotiation, do the following steps:</span></span>  
  
1. <span data-ttu-id="1963e-175">將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> 以實作委派。</span><span class="sxs-lookup"><span data-stu-id="1963e-175">Implement delegation by setting <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span>  
  
2. <span data-ttu-id="1963e-176">要求 SSPI 交涉：</span><span class="sxs-lookup"><span data-stu-id="1963e-176">Require SSPI negotiation:</span></span>  
  
    1.  <span data-ttu-id="1963e-177">如果您是使用標準繫結，請將 `NegotiateServiceCredential` 屬性 (Property) 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1963e-177">If you are using standard bindings, set the `NegotiateServiceCredential` property to `true`.</span></span>  
  
    2.  <span data-ttu-id="1963e-178">如果您是使用自訂繫結，請將 `AuthenticationMode` 項目的 `Security` 屬性 (Attribute) 設定為 `SspiNegotiated`。</span><span class="sxs-lookup"><span data-stu-id="1963e-178">If you are using custom bindings, set the `AuthenticationMode` attribute of the `Security` element to `SspiNegotiated`.</span></span>  
  
3. <span data-ttu-id="1963e-179">透過拒絕使用 NTLM 來要求 SSPI 交涉使用 Kerberos：</span><span class="sxs-lookup"><span data-stu-id="1963e-179">Require the SSPI negotiation to use Kerberos by disallowing the use of NTLM:</span></span>  
  
    1.  <span data-ttu-id="1963e-180">在程式碼中使用下列陳述式來做到這點：`ChannelFactory.Credentials.Windows.AllowNtlm = false`</span><span class="sxs-lookup"><span data-stu-id="1963e-180">Do this in code, with the following statement: `ChannelFactory.Credentials.Windows.AllowNtlm = false`</span></span>  
  
    2.  <span data-ttu-id="1963e-181">或者，您可以將組態檔中的 `allowNtlm` 屬性設定為 `false` 來做到這點。</span><span class="sxs-lookup"><span data-stu-id="1963e-181">Or you can do this in the configuration file by setting the `allowNtlm` attribute to `false`.</span></span> <span data-ttu-id="1963e-182">此屬性包含在[ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)。</span><span class="sxs-lookup"><span data-stu-id="1963e-182">This attribute is contained in the [\<windows>](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).</span></span>  
  
### <a name="ntlm-protocol"></a><span data-ttu-id="1963e-183">NTLM 通訊協定</span><span class="sxs-lookup"><span data-stu-id="1963e-183">NTLM Protocol</span></span>  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a><span data-ttu-id="1963e-184">交涉 SSP 退而使用 NTLM，但是 NTLM 已停用</span><span class="sxs-lookup"><span data-stu-id="1963e-184">Negotiate SSP Falls Back to NTLM, but NTLM Is Disabled</span></span>  
 <span data-ttu-id="1963e-185"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>屬性設定為`false`，這樣會使 Windows Communication Foundation (WCF) 讓最大努力擲回例外狀況，如果使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="1963e-185">The <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property is set to `false`, which causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="1963e-186">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="1963e-186">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>  
  
 <span data-ttu-id="1963e-187">下列程式碼示範如何停用退回使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="1963e-187">The following shows how to disable fallback to NTLM.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a><span data-ttu-id="1963e-188">NTLM 登入失敗</span><span class="sxs-lookup"><span data-stu-id="1963e-188">NTLM Logon Fails</span></span>  
 <span data-ttu-id="1963e-189">用戶端認證在服務上屬於無效。</span><span class="sxs-lookup"><span data-stu-id="1963e-189">The client credentials are not valid on the service.</span></span> <span data-ttu-id="1963e-190">請檢查使用者名稱與密碼是否有正確設定，以及是否有對應到服務執行所在電腦所認得的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1963e-190">Check that the user name and password are correctly set and correspond to an account that is known to the computer where the service is running.</span></span> <span data-ttu-id="1963e-191">NTLM 會使用指定的認證來登入該服務的電腦。</span><span class="sxs-lookup"><span data-stu-id="1963e-191">NTLM uses the specified credentials to log on to the service's computer.</span></span> <span data-ttu-id="1963e-192">儘管在用戶端執行所在電腦上的認證可能是有效的，如果該認證在服務的電腦上屬於無效，這項登入仍然會失敗。</span><span class="sxs-lookup"><span data-stu-id="1963e-192">While the credentials may be valid on the computer where the client is running, this logon will fail if the credentials are not valid on the service's computer.</span></span>  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a><span data-ttu-id="1963e-193">發生匿名 NTLM 登入，不過匿名登入已依預設地停用。</span><span class="sxs-lookup"><span data-stu-id="1963e-193">Anonymous NTLM Logon Occurs, but Anonymous Logons Are Disabled by Default</span></span>  
 <span data-ttu-id="1963e-194">當建立用戶端時，<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 屬性已設定為 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>，但是伺服器卻已依預設地拒絕匿名登入，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1963e-194">When creating a client, the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property is set to <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, as shown in the following example, but by default the server disallows anonymous logons.</span></span> <span data-ttu-id="1963e-195">這種情況的發生原因在於 <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> 類別之 <xref:System.ServiceModel.Security.WindowsServiceCredential> 屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1963e-195">This occurs because the default value of the <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> property of the <xref:System.ServiceModel.Security.WindowsServiceCredential> class is `false`.</span></span>  
  
 <span data-ttu-id="1963e-196">下列用戶端程式碼會嘗試啟用匿名登入 (請注意，預設屬性是 `Identification`)。</span><span class="sxs-lookup"><span data-stu-id="1963e-196">The following client code attempts to enable anonymous logons (note that the default property is `Identification`).</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 <span data-ttu-id="1963e-197">下列服務程式碼會變更預設值，讓伺服器允許匿名登入。</span><span class="sxs-lookup"><span data-stu-id="1963e-197">The following service code changes the default to enable anonymous logons by the server.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 <span data-ttu-id="1963e-198">如需有關模擬的詳細資訊，請參閱 <<c0> [ 委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="1963e-198">For more information about impersonation, see [Delegation and Impersonation](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="1963e-199">或者，用戶端會使用內建帳戶 SYSTEM 來執行為 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="1963e-199">Alternatively, the client is running as a Windows service, using the built-in account SYSTEM.</span></span>  
  
### <a name="other-problems"></a><span data-ttu-id="1963e-200">其他問題</span><span class="sxs-lookup"><span data-stu-id="1963e-200">Other Problems</span></span>  
  
#### <a name="client-credentials-are-not-set-correctly"></a><span data-ttu-id="1963e-201">用戶端認證沒有正確設定</span><span class="sxs-lookup"><span data-stu-id="1963e-201">Client Credentials Are Not Set Correctly</span></span>  
 <span data-ttu-id="1963e-202">Windows 驗證使用由 <xref:System.ServiceModel.Security.WindowsClientCredential> 類別之 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性傳回的 <xref:System.ServiceModel.ClientBase%601> 執行個體，而不是使用 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>。</span><span class="sxs-lookup"><span data-stu-id="1963e-202">Windows authentication uses the <xref:System.ServiceModel.Security.WindowsClientCredential> instance returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class, not the <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.</span></span> <span data-ttu-id="1963e-203">下面舉出不正確的範例。</span><span class="sxs-lookup"><span data-stu-id="1963e-203">The following shows an incorrect example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 <span data-ttu-id="1963e-204">下面舉出正確的範例。</span><span class="sxs-lookup"><span data-stu-id="1963e-204">The following shows the correct example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a><span data-ttu-id="1963e-205">無法使用 SSPI</span><span class="sxs-lookup"><span data-stu-id="1963e-205">SSPI Is Not Available</span></span>  
 <span data-ttu-id="1963e-206">在下列作業系統不支援 Windows 驗證時用來作為伺服器：[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition， [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition 和[!INCLUDE[wv](../../../../includes/wv-md.md)]Home edition。</span><span class="sxs-lookup"><span data-stu-id="1963e-206">The following operating systems do not support Windows authentication when used as a server: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition, and [!INCLUDE[wv](../../../../includes/wv-md.md)]Home editions.</span></span>  
  
#### <a name="developing-and-deploying-with-different-identities"></a><span data-ttu-id="1963e-207">以不同的身分進行開發及部署</span><span class="sxs-lookup"><span data-stu-id="1963e-207">Developing and Deploying with Different Identities</span></span>  
 <span data-ttu-id="1963e-208">如果您在某一台電腦上開發應用程式，然後又在另一台電腦上進行部署，而且在每一台電腦上都使用不同的帳戶類型進行驗證，您可能會產生不同的行為。</span><span class="sxs-lookup"><span data-stu-id="1963e-208">If you develop your application on one machine, and deploy on another, and use different account types to authenticate on each machine, you may experience different behavior.</span></span> <span data-ttu-id="1963e-209">例如，假設您是使用 `SSPI Negotiated`驗證模式，在 Windows XP Pro 機器上開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="1963e-209">For example, suppose you develop your application on a Windows XP Pro machine using the `SSPI Negotiated` authentication mode.</span></span> <span data-ttu-id="1963e-210">您又使用本機使用者帳戶進行身分驗證，然後又使用了 NTLM 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1963e-210">If you use a local user account to authenticate with, then NTLM protocol will be used.</span></span> <span data-ttu-id="1963e-211">應用程式開發完成後，您以網域帳戶先在 Windows Server 2003 機器上部署服務而後執行。</span><span class="sxs-lookup"><span data-stu-id="1963e-211">Once the application is developed, you deploy the service to a Windows Server 2003 machine where it runs under a domain account.</span></span> <span data-ttu-id="1963e-212">此時，用戶端將無法驗證該服務，因為用戶端使用的是 Kerberos 及網域控制站。</span><span class="sxs-lookup"><span data-stu-id="1963e-212">At this point the client will not be able to authenticate the service because it will be using Kerberos and a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1963e-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1963e-213">See also</span></span>

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="1963e-214">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="1963e-214">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [<span data-ttu-id="1963e-215">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="1963e-215">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
