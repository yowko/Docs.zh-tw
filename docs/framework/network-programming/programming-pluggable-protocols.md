---
title: "可插式通訊協定程式設計 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "下載網際網路資源，可插式通訊協定"
  - "WebRequest 類別，可插式通訊協定"
  - "網際網路要求回應，可插式通訊協定"
  - "WebResponse 類別，可插式通訊協定"
  - "傳送資料，可插式通訊協定"
  - "網路資源，可插式通訊協定"
  - "網際網路，可插式通訊協定"
  - "可插式通訊協定程式設計"
  - "可插式通訊協定，程式設計"
  - "從網際網路要求資料，可插式通訊協定"
  - "接收資料，可插式通訊協定"
  - "通訊協定，可插式"
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 可插式通訊協定程式設計
抽象 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供可外掛式通訊協定提供為基底。  藉由衍生通訊協定的特定類別從 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>，應用程式可以從網際網路資源要求資料和讀取回應，而不指定要使用的通訊協定。  
  
 在建立通訊協定專屬的 <xref:System.Net.WebRequest>之前，您必須註冊其建立方法。  使用 <xref:System.Net.WebRequest> 靜態 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> 方法註冊 <xref:System.Net.WebRequest> 子代處理一組需求加入至特定網際網路計劃，加入計劃和伺服器，或加入至計劃、伺服器和路徑。  
  
 在許多情況下，您可以傳送和接收資料 <xref:System.Net.WebRequest> 使用的方法和屬性的類別。  不過，因此，如果您需要存取通訊協定的特定屬性，您可以將指標的型別 <xref:System.Net.WebRequest> 角色加入至特定衍生類別的執行個體。  
  
 若要利用可外掛式通訊協定，您的 <xref:System.Net.WebRequest> 子代必須提供不需要通訊協定的特定屬性設定的預設要求和回應交易。  例如， <xref:System.Net.HttpWebRequest> 類別，根據預設 <xref:System.Net.WebRequest> HTTP 實作的類別，以提供包含從 Web 伺服器所傳回的資料流上的 `GET` 要求並傳回 <xref:System.Net.HttpWebResponse> 。  
  
## 請參閱  
 [衍生自 WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)   
 [衍生自 WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)   
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)   
 [如何：轉換 WebRequest 類型以存取通訊協定特定屬性](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)