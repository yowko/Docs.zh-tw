---
title: HOW TO：將合約公開給 SOAP 和 Web 用戶端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>HOW TO：將合約公開給 SOAP 和 Web 用戶端
根據預設，Windows Communication Foundation (WCF) 提供端點只對 SOAP 用戶端。 在[How to： 建立基本的 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)，端點都可以提供給非 SOAP 用戶端。 有時候您可能會想要讓兩者都有機會使用相同合約，也就是同時當做 Web 端點和 SOAP 端點。 本主題說明如何執行此操作的範例。  
  
### <a name="to-define-the-service-contract"></a>若要定義服務合約  
  
1.  透過加上 <xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute> 和 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標示的介面來定義服務合約，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  根據預設，<xref:System.ServiceModel.Web.WebInvokeAttribute> 會將 POST 呼叫對應至作業。 但是，您可以指定 "method=" 參數，以指定要對應至作業的方法。 <xref:System.ServiceModel.Web.WebGetAttribute> 沒有 "method=" 參數，只能將 GET 呼叫對應至服務作業。  
  
2.  實作服務合約，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>若要裝載服務  
  
1.  建立 <xref:System.ServiceModel.ServiceHost> 物件，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  針對 SOAP 端點加入具有 <xref:System.ServiceModel.Description.ServiceEndpoint> 的 <xref:System.ServiceModel.BasicHttpBinding>，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  針對非 SOAP 端點加入具有 <xref:System.ServiceModel.Description.ServiceEndpoint> 的 <xref:System.ServiceModel.WebHttpBinding>，並將 <xref:System.ServiceModel.Description.WebHttpBehavior> 加入至端點，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  在 `Open()` 執行個體上呼叫 <xref:System.ServiceModel.ServiceHost> 以開啟服務主機，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>若要在 Internet Explorer 中呼叫對應至 GET 的服務作業  
  
1.  開啟 Internet Explorer 並輸入"`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`"然後按 ENTER。 URL 包含服務的基底位址 ("http://localhost:8000/")，端點的相對位址 ("")，以連字號分隔的具名參數清單後面接著要呼叫 ("EchoWithGet") 和問號的服務作業 (&)。  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>若要透過程式碼呼叫 Web 端點上的服務作業  
  
1.  在 <xref:System.ServiceModel.Web.WebChannelFactory%601> 區塊內建立 `using` 的執行個體，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  在 `Close()` 區塊結尾，會在通道上自動呼叫 `using`。  
  
1.  建立通道並呼叫服務，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>若要在 SOAP 端點上呼叫服務作業  
  
1.  在 <xref:System.ServiceModel.ChannelFactory> 區塊內建立 `using` 的執行個體，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  建立通道並呼叫服務，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>若要關閉服務主機  
  
1.  關閉服務主機，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>範例  
 以下是這個主題的完整程式碼清單。  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 編譯 Service.cs 時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
