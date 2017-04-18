---
title: "建立 WS-I Basic Profile 1.1 互通服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組態 [WCF], 互通的服務"
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 建立 WS-I Basic Profile 1.1 互通服務
將 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務端點設成與 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web 服務用戶端互通：  
  
-   使用<xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>作為您的服務端點的繫結型別類型。  
  
-   請勿使用回呼與工作階段合約功能，或在您服務端點上的交易行為  
  
 您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。  
  
 下列功能的<xref:System.ServiceModel.BasicHttpBinding>類別要求的功能無法 WS-Basic Profile 1.1:  
  
-   訊息傳輸最佳化機制 (MTOM) 訊息編碼受到<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=fullName>屬性。 將此屬性保留其預設值，亦即<xref:System.ServiceModel.WSMessageEncoding?displayProperty=fullName>不使用 MTOM。  
  
-   訊息安全性受到<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=fullName>值提供符合 WS-I Ws-security 支援-Basic Security Profile 1.0。 將此屬性保留其預設值，亦即<xref:System.ServiceModel.SecurityMode?displayProperty=fullName>為不使用 Ws-security。  
  
 若要將中繼資料給[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]可用來服務[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，使用 Web 服務用戶端產生工具︰ [Web 服務描述語言工具 (Wsdl.exe)](http://msdn.microsoft.com/zh-tw/b9210348-8bc2-4367-8c91-d1a04b403e88)， [Web 服務探索工具 (Disco.exe)](http://msdn.microsoft.com/zh-tw/acd88078-c581-42bc-94ca-6633e2851979)，而`Add Web Reference`功能[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; 您必須啟用發行中繼資料。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][發行中繼資料端點](../../../docs/framework/wcf/publishing-metadata-endpoints.md)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下例範例程式碼示範如何在程式碼中，或是組態檔案中新增與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web 服務用戶端相容的 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 端點。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
  
 [!code[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/common/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>另請參閱  
 [與 ASP.NET Web 服務的互通性](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)