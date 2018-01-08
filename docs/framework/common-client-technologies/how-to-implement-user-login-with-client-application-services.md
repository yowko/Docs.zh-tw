---
title: "如何：使用用戶端應用程式服務實作使用者登入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bf073b6db0a69cfda0c69ae34df0396f5dea35c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-user-login-with-client-application-services"></a><span data-ttu-id="49deb-102">如何：使用用戶端應用程式服務實作使用者登入</span><span class="sxs-lookup"><span data-stu-id="49deb-102">How to: Implement User Login with Client Application Services</span></span>
<span data-ttu-id="49deb-103">您可以透過現有 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務，使用用戶端應用程式服務來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="49deb-103">You can use client application services to validate users through an existing [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profile service.</span></span> <span data-ttu-id="49deb-104">如需如何設定 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務的資訊，請參閱[使用表單驗證搭配Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)。</span><span class="sxs-lookup"><span data-stu-id="49deb-104">For information about how to set up the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profile service, see [Using Forms Authentication with Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).</span></span>  
  
 <span data-ttu-id="49deb-105">下列程序描述當應用程式設定為使用其中一個用戶端驗證服務提供者時，如何透過驗證服務驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="49deb-105">The following procedures describe how to validate users through the authentication service when your application is configured to use one of the client authentication service providers.</span></span> <span data-ttu-id="49deb-106">如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="49deb-106">For more information, see [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span>  
  
 <span data-ttu-id="49deb-107">您通常會透過 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法執行所有驗證。</span><span class="sxs-lookup"><span data-stu-id="49deb-107">You will typically perform all validation through the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="49deb-108">這個方法會透過已設定的驗證提供者管理與驗證服務的互動。</span><span class="sxs-lookup"><span data-stu-id="49deb-108">This method manages the interaction with the authentication service through the configured authentication provider.</span></span> <span data-ttu-id="49deb-109">如需詳細資訊，請參閱[用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="49deb-109">For more information, see [Client Application Services Overview](../../../docs/framework/common-client-technologies/client-application-services-overview.md).</span></span>  
  
 <span data-ttu-id="49deb-110">表單驗證程序需要存取執行中的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 驗證服務。</span><span class="sxs-lookup"><span data-stu-id="49deb-110">The forms authentication procedures require access to a running [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] authentication service.</span></span> <span data-ttu-id="49deb-111">如需端對端測試用戶端應用程式服務功能，請參閱[逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="49deb-111">For guidance on end-to-end testing of client application services features, see [Walkthrough: Using Client Application Services](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span></span>  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a><span data-ttu-id="49deb-112">以使用成員資格認證提供者的表單驗證來驗證使用者</span><span class="sxs-lookup"><span data-stu-id="49deb-112">To authenticate a user with forms authentication using a membership credentials provider</span></span>  
  
1.  <span data-ttu-id="49deb-113">實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面。</span><span class="sxs-lookup"><span data-stu-id="49deb-113">Implement the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interface.</span></span> <span data-ttu-id="49deb-114">下列程式碼範例示範衍生自 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> 之對話方塊類別的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="49deb-114">The following code example shows a <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementation for a login dialog box class derived from  <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49deb-115">這個對話方塊提供可輸入使用者名稱與密碼的文字方塊，以及 [記住我] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="49deb-115">This dialog box has text boxes for user name and password and a "remember me" check box.</span></span> <span data-ttu-id="49deb-116">當用戶端驗證提供者呼叫 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法時，表單便會顯示。</span><span class="sxs-lookup"><span data-stu-id="49deb-116">When the client authentication provider calls the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> method, the form is displayed.</span></span> <span data-ttu-id="49deb-117">使用者在登入對話方塊中填入資訊然後按一下 [確定] 後，就會在新的 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> 物件中傳回指定的值。</span><span class="sxs-lookup"><span data-stu-id="49deb-117">When the user fills in the information in the login dialog box and clicks OK, the specified values are returned in a new <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> object.</span></span>  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  <span data-ttu-id="49deb-118">呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後以空字串當做參數值傳入。</span><span class="sxs-lookup"><span data-stu-id="49deb-118">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass in empty strings as the parameter values.</span></span> <span data-ttu-id="49deb-119">當您指定空字串時，這個方法會針對為應用程式所設定之認證提供者，於內部呼叫 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="49deb-119">When you specify empty strings, this method internally calls the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> method for the credentials provider configured for your application.</span></span> <span data-ttu-id="49deb-120">下列程式碼範例會呼叫這個方法，限制存取整個 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="49deb-120">The following code example calls this method to restrict access to an entire Windows Forms application.</span></span> <span data-ttu-id="49deb-121">您可以將這段程式碼加入 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 處理常式。</span><span class="sxs-lookup"><span data-stu-id="49deb-121">You can add this code to a <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> handler.</span></span>  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a><span data-ttu-id="49deb-122">以不使用成員資格認證提供者的表單驗證來驗證使用者</span><span class="sxs-lookup"><span data-stu-id="49deb-122">To authenticate a user with forms authentication without using a membership credentials provider</span></span>  
  
-   <span data-ttu-id="49deb-123">呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後傳入從使用者處擷取的使用者名稱與密碼值。</span><span class="sxs-lookup"><span data-stu-id="49deb-123">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass in user name and password values retrieved from the user.</span></span>  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a><span data-ttu-id="49deb-124">以 Windows 驗證來驗證使用者</span><span class="sxs-lookup"><span data-stu-id="49deb-124">To authenticate a user with Windows authentication</span></span>  
  
-   <span data-ttu-id="49deb-125">呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後傳遞空字串的參數。</span><span class="sxs-lookup"><span data-stu-id="49deb-125">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass empty strings for the parameters.</span></span> <span data-ttu-id="49deb-126">這個方法呼叫一定會傳回 `true`，並且將 Cookie 加入其中包含 Windows 識別之使用者的 Cookie 快取中。</span><span class="sxs-lookup"><span data-stu-id="49deb-126">This method call will always return `true` and will add a cookie to the user's cookie cache that contains the Windows identity.</span></span>  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a><span data-ttu-id="49deb-127">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="49deb-127">Robust Programming</span></span>  
 <span data-ttu-id="49deb-128">這個主題中的範例程式碼會示範 Windows 用戶端應用程式中驗證的最簡單用法。</span><span class="sxs-lookup"><span data-stu-id="49deb-128">The example code in this topic demonstrates the simplest usages of authentication in a Windows client application.</span></span> <span data-ttu-id="49deb-129">當您使用用戶端應用程式服務與表單驗證呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法時，您的程式碼可能會擲回 <xref:System.Net.WebException>。</span><span class="sxs-lookup"><span data-stu-id="49deb-129">When you call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method with client application services and forms authentication, however, your code can throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="49deb-130">這表示驗證服務無法使用。</span><span class="sxs-lookup"><span data-stu-id="49deb-130">This indicates that the authentication service is unavailable.</span></span> <span data-ttu-id="49deb-131">如需如何處理這個例外狀況的範例，請參閱[逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)。</span><span class="sxs-lookup"><span data-stu-id="49deb-131">For an example of how to handle this exception, see [Walkthrough: Using Client Application Services](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49deb-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="49deb-132">See Also</span></span>  
 [<span data-ttu-id="49deb-133">用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="49deb-133">Client Application Services</span></span>](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [<span data-ttu-id="49deb-134">用戶端應用程式服務概觀</span><span class="sxs-lookup"><span data-stu-id="49deb-134">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [<span data-ttu-id="49deb-135">如何：設定用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="49deb-135">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [<span data-ttu-id="49deb-136">逐步解說：使用用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="49deb-136">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [<span data-ttu-id="49deb-137">使用表單驗證搭配 Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="49deb-137">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
