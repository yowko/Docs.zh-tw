---
title: "HOW TO：將合約公開給 SOAP 和 Web 用戶端 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# HOW TO：將合約公開給 SOAP 和 Web 用戶端
根據預設，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 只會讓 SOAP 用戶端使用端點。  在 [HOW TO：建立基本 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)中，端點可提供給非 SOAP 用戶端使用。  有時候您可能會想要讓兩者都有機會使用相同合約，也就是同時當做 Web 端點和 SOAP 端點。  本主題說明如何執行此操作的範例。  
  
### 若要定義服務合約  
  
1.  透過加上 <xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute> 和 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標示的介面來定義服務合約，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  根據預設，<xref:System.ServiceModel.Web.WebInvokeAttribute> 會將 POST 呼叫對應至作業。  但是，您可以指定 "method\=" 參數，以指定要對應至作業的方法。  <xref:System.ServiceModel.Web.WebGetAttribute> 沒有 "method\=" 參數，只能將 GET 呼叫對應至服務作業。  
  
2.  實作服務合約，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### 若要裝載服務  
  
1.  建立 <xref:System.ServiceModel.ServiceHost> 物件，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  針對 SOAP 端點加入具有 <xref:System.ServiceModel.BasicHttpBinding> 的 <xref:System.ServiceModel.Description.ServiceEndpoint>，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  針對非 SOAP 端點加入具有 <xref:System.ServiceModel.WebHttpBinding> 的 <xref:System.ServiceModel.Description.ServiceEndpoint>，並將 <xref:System.ServiceModel.Description.WebHttpBehavior> 加入至端點，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  在 <xref:System.ServiceModel.ServiceHost> 執行個體上呼叫 `Open()` 以開啟服務主機，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### 若要在 Internet Explorer 中呼叫對應至 GET 的服務作業  
  
1.  開啟 Internet Explorer 並輸入 "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`"，然後按 ENTER。  URL 包含服務的基底位址 \("http:\/\/localhost:8000\/"\)、端點的相對位址 \(""\)、要呼叫的服務作業 \("EchoWithGet"\)、問號，並於後面接續由連字號 \(&\) 分隔的具名參數清單。  
  
### 若要透過程式碼呼叫 Web 端點上的服務作業  
  
1.  在 `using` 區塊內建立 <xref:System.ServiceModel.Web.WebChannelFactory%601> 的執行個體，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  在 `using` 區塊結尾，會在通道上自動呼叫 `Close()`。  
  
1.  建立通道並呼叫服務，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### 若要在 SOAP 端點上呼叫服務作業  
  
1.  在 `using` 區塊內建立 <xref:System.ServiceModel.ChannelFactory> 的執行個體，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  建立通道並呼叫服務，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### 若要關閉服務主機  
  
1.  關閉服務主機，如下列程式碼所示。  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## 範例  
 以下是這個主題的完整程式碼清單。  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## 編譯程式碼  
 編譯 Service.cs 時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。  
  
## 請參閱  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Web.WebGetAttribute>   
 <xref:System.ServiceModel.Web.WebInvokeAttribute>   
 <xref:System.ServiceModel.Web.WebServiceHost>   
 <xref:System.ServiceModel.ChannelFactory>   
 <xref:System.ServiceModel.Description.WebHttpBehavior>   
 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)