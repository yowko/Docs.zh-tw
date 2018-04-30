---
title: HOW TO：使用雙工合約存取服務
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
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c80980ff5a5b1011c021bcaf0688747178ec5b9b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>HOW TO：使用雙工合約存取服務
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 其中一項功能，就是建立使用雙工訊息模式的服務。 這個模式可讓服務透過回呼與用戶端通訊。 本主題將說明在會實作回呼介面的用戶端類別中，建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的步驟。  
  
 雙重繫結會向服務公開用戶端的 IP 位址， 用戶端應該利用安全性來確保它只與信任的服務連接。  
  
 如需建立基本的教學課程[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務與用戶端，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。  
  
### <a name="to-access-a-duplex-service"></a>若要存取雙工服務  
  
1.  建立包含兩個介面的服務。 第一個介面主要供服務使用，第二個則是供回呼使用。 如需有關建立雙工服務的詳細資訊，請參閱[How to： 建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
2.  執行服務。  
  
3.  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端合約 （介面）。 如需如何執行這項操作資訊，請參閱[How to： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
4.  依下列範例所示，在用戶端類別中實作回呼介面。  
  
    ```csharp  
    public class CallbackHandler : ICalculatorDuplexCallback  
    {  
        public void Result(double result)  
        {  
            Console.WriteLine("Result ({0})", result);  
        }  
        public void Equation(string equation)  
        {  
            Console.WriteLine("Equation({0})", equation);  
        }  
    }  
    ```  
  
    ```vb  
    Public Class CallbackHandler   
    Implements ICalculatorDuplexCallback  
       Public Sub Result (ByVal result As Double)  
          Console.WriteLine("Result ({0})", result)  
       End Sub  
        Public Sub Equation(ByVal equation As String)  
            Console.Writeline("Equation({0})", equation)  
        End Sub  
    End Class  
    ```  
  
5.  建立 <xref:System.ServiceModel.InstanceContext> 類別的執行個體。 建構函式需要用戶端類別的執行個體。  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  使用需要 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 物件的建構函式來建立 <xref:System.ServiceModel.InstanceContext> 用戶端的執行個體。 建構函式的第二個參數就是組態檔中找到的端點名稱。  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  視需要呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範如何建立會存取雙工合約的用戶端類別。  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
  
## <a name="see-also"></a>另請參閱  
 [快速入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [如何：建立雙面合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [如何：建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [如何：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
