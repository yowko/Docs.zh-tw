---
title: 如何：使用用戶端應用程式服務實作使用者登入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
ms.openlocfilehash: a878b12620faf9a6e9fecbd2e76644aea3d80611
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504792"
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>如何：使用用戶端應用程式服務實作使用者登入
您可以透過現有 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務，使用用戶端應用程式服務來驗證使用者。 如需如何設定 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務的資訊，請參閱[使用表單驗證搭配Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)。  
  
 下列程序描述當應用程式設定為使用其中一個用戶端驗證服務提供者時，如何透過驗證服務驗證使用者。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。  
  
 您通常會透過 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法執行所有驗證。 這個方法會透過已設定的驗證提供者管理與驗證服務的互動。 如需詳細資訊，請參閱[用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)。  
  
 表單驗證程序需要存取執行中的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 驗證服務。 如需端對端測試用戶端應用程式服務功能，請參閱[逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)。  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>以使用成員資格認證提供者的表單驗證來驗證使用者  
  
1.  實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面。 下列程式碼範例示範衍生自 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> 之對話方塊類別的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> 實作。 這個對話方塊提供可輸入使用者名稱與密碼的文字方塊，以及 [記住我] 核取方塊。 當用戶端驗證提供者呼叫 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法時，表單便會顯示。 使用者在登入對話方塊中填入資訊然後按一下 [確定] 後，就會在新的 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> 物件中傳回指定的值。  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後以空字串當做參數值傳入。 當您指定空字串時，這個方法會針對為應用程式所設定之認證提供者，於內部呼叫 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法。 下列程式碼範例會呼叫這個方法，限制存取整個 Windows Form 應用程式。 您可以將這段程式碼加入 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 處理常式。  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>以不使用成員資格認證提供者的表單驗證來驗證使用者  
  
-   呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後傳入從使用者處擷取的使用者名稱與密碼值。  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>以 Windows 驗證來驗證使用者  
  
-   呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法，然後傳遞空字串的參數。 這個方法呼叫一定會傳回 `true`，並且將 Cookie 加入其中包含 Windows 識別之使用者的 Cookie 快取中。  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 這個主題中的範例程式碼會示範 Windows 用戶端應用程式中驗證的最簡單用法。 當您使用用戶端應用程式服務與表單驗證呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法時，您的程式碼可能會擲回 <xref:System.Net.WebException>。 這表示驗證服務無法使用。 如需如何處理這個例外狀況的範例，請參閱[逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)。  
  
## <a name="see-also"></a>請參閱  
 [用戶端應用程式服務](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [使用表單驗證搭配 Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
