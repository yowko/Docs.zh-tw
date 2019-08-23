---
title: HOW TO：在服務上模擬用戶端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 918cbba30cbb997a1f029a250adbdc4ed6310299
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951050"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="ef3c5-102">HOW TO：在服務上模擬用戶端</span><span class="sxs-lookup"><span data-stu-id="ef3c5-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="ef3c5-103">在 Windows Communication Foundation (WCF) 服務上模擬用戶端, 可讓服務代表用戶端執行動作。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-103">Impersonating a client on a Windows Communication Foundation (WCF) service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="ef3c5-104">關於存取控制清單 (ACL) 檢查的動作，例如存取機器上的目錄和檔案或存取 SQL Server 資料庫，請根據用戶端使用者帳戶檢查 ACL。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="ef3c5-105">本主題說明在 Windows 網域中啟用用戶端以設定用戶端模擬等級所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="ef3c5-106">如需此文件的實用範例，請參閱 [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> <span data-ttu-id="ef3c5-107">如需有關用戶端模擬的詳細資訊, 請參閱[委派和](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)模擬。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-107">For more information about client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef3c5-108">用戶端和服務在相同電腦上執行，且用戶端在系統帳戶下執行時 (也就是 `Local System` 或 `Network Service`)，以可設定狀態的安全性內容權杖建立安全的工作階段時無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="ef3c5-109">WinForms 或主控台應用程式通常在目前登入的帳戶下執行，因此根據預設值可以模擬該帳戶。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="ef3c5-110">不過, 當用戶端是 ASP.NET 網頁, 而且該頁面裝載于 iis 6.0 或 iis 7.0 中時, 用戶端預設會在`Network Service`帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-110">However, when the client is an ASP.NET page and that page is hosted in IIS 6.0 or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="ef3c5-111">所有支援安全工作階段的系統提供繫結預設為使用沒有狀態的安全性內容權杖。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="ef3c5-112">不過, 如果用戶端是 ASP.NET 網頁, 而且使用具有可設定狀態之安全性內容權杖的安全會話, 就無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-112">However, if the client is an ASP.NET page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> <span data-ttu-id="ef3c5-113">如需在安全會話中使用可設定狀態之安全性內容權杖的[詳細資訊, 請參閱如何:為安全會話](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)建立安全性內容權杖。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-113">For more information about using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="ef3c5-114">若要從服務上的快取 Windows 權杖啟用用戶端模擬</span><span class="sxs-lookup"><span data-stu-id="ef3c5-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1. <span data-ttu-id="ef3c5-115">建立服務。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-115">Create the service.</span></span> <span data-ttu-id="ef3c5-116">如需此基本程序的教學課程，請參閱 [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2. <span data-ttu-id="ef3c5-117">使用運用 Windows 驗證並建立工作階段的繫結，例如 <xref:System.ServiceModel.NetTcpBinding> 或 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="ef3c5-118">建立服務的介面實作時，將 <xref:System.ServiceModel.OperationBehaviorAttribute> 類別套用至需要用戶端模擬的方法。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="ef3c5-119">將 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 屬性設定為 <xref:System.ServiceModel.ImpersonationOption.Required>。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="ef3c5-120">若要設定用戶端上的允許模擬等級</span><span class="sxs-lookup"><span data-stu-id="ef3c5-120">To set the allowed impersonation level on the client</span></span>  
  
1. <span data-ttu-id="ef3c5-121">使用 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立服務用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="ef3c5-122">如需詳細資訊, 請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-122">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="ef3c5-123">建立 WCF 用戶端之後, 請將<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.ServiceModel.Security.WindowsClientCredential> <xref:System.Security.Principal.TokenImpersonationLevel>類別的屬性設定為其中一個列舉值。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-123">After creating the WCF client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ef3c5-124">若要使用 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>，必須使用交涉的 Kerberos 驗證 (有時稱為 *multi-leg* 或 *multi-step* Kerberos)。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="ef3c5-125">如需如何執行此操作的說明, 請參閱[安全性的最佳作法](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3c5-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef3c5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef3c5-126">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [<span data-ttu-id="ef3c5-127">模擬用戶端</span><span class="sxs-lookup"><span data-stu-id="ef3c5-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [<span data-ttu-id="ef3c5-128">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="ef3c5-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
