---
title: HOW TO：使用 X.509 憑證來確保服務安全
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
caps.latest.revision: 8
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 89ad47ad898184b99f32743855091c0985722f77
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>HOW TO：使用 X.509 憑證來確保服務安全
使用 X.509 憑證確保服務安全是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中大部分繫結使用的基本技術。 此主題會介紹使用 X.509 憑證設定自我主控服務的步驟。  
  
 必要條件是能夠用來驗證伺服器的有效憑證。 憑證必須透過受信任的憑證授權單位發行至伺服器。 如果憑證無效，任何嘗試使用服務的用戶端都不會信任該服務，因此無法建立連線。 如需有關如何使用憑證的詳細資訊，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>使用程式碼搭配憑證設定服務  
  
1.  建立服務合約以及實作的服務。 如需詳細資訊，請參閱[設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)。  
  
2.  建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode.Message>，如下列程式碼所示。  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  建立兩個 <xref:System.Type> 變數，分別指派給合約類型以及已實作合約，如下列程式碼所示。  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  建立服務基底位址之 <xref:System.Uri> 類別的執行個體。 因為 `WSHttpBinding` 會使用 HTTP 傳輸，所以統一資源識別元 (URI) 必須以這個結構描述開頭，否則當開啟服務時 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 將擲回例外狀況。  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  使用已實作之合約類型變數與 URI 建立 <xref:System.ServiceModel.ServiceHost> 類別的新執行個體。  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  使用 <xref:System.ServiceModel.Description.ServiceEndpoint> 方法將 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 新增至服務。 將合約、繫結，以及端點位址傳遞給建構函式，如下列程式碼所示。  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  選擇性。 若要從服務擷取中繼資料，請建立新的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 物件並將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true`。  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  請使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，將有效憑證新增至服務。 方法就可以使用其中一種方法尋找憑證。 這個範例會使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> 列舉。 列舉會指定所提供的值，是憑證所發行至該實體的名稱。  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. 呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 方法啟動服務接聽。 如果您建立主控台應用程式，請呼叫 <xref:System.Console.ReadLine%2A> 方法讓服務保持在接聽狀態。  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法，使用 X.509 憑證設定服務。  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 要編譯程式碼時，必須有下列命名空間：  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>另請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
