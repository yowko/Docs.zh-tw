---
title: "自訂訊息格式器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 自訂訊息格式器
訊息中的內容常使用 XML 格式，這對於應用程式通常並不方便。  應用程式會操作物件，取得及設定其屬性。  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用「*資料合約*」\(Data Contract\) 來將 <xref:System.ServiceModel.Channels.Message> 物件轉換成應用程式容易處理的物件。  這些處理程序稱為序列化和還原序列化。  請注意，這些相同的詞彙用於描述由傳輸層在往來訊息 Wire 格式之間進行的序列化和還原序列化，是不相關的處理程序。  
  
 如果您需要實作無法使用資料合約完成的訊息和物件之間的特定轉換，可以使用自訂訊息格式器。  如果要執行這項操作，請在用戶端或服務上修改或延伸特定合約作業的執行行為。  
  
## 用戶端上的自訂訊息格式器  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 介面會定義方法，用於控制用戶端應用程式的訊息與物件之間的轉換。  
  
 您必須實作這個介面。  首先請覆寫 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> 方法，以還原序列化訊息。  在收到傳入訊息之後、分派到用戶端作業之前會呼叫這個方法。  
  
 接下來，覆寫 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> 方法以序列化物件。  在傳送傳出訊息之前會呼叫這個方法。  
  
 如果要將自訂格式器插入服務應用程式中，請使用作業行為將 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 物件指派給 <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> 屬性。  如需行為的資訊，請參閱[使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## 服務上的自訂訊息格式器  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 介面會定義將 <xref:System.ServiceModel.Channels.Message> 物件轉換成作業的參數，以及從參數轉換成 <xref:System.ServiceModel.Channels.Message> 服務應用程式中物件的方法。  
  
 您必須實作這個介面。  首先請覆寫 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> 方法，以還原序列化訊息。  在收到傳入訊息之後、分派到用戶端作業之前會呼叫這個方法。  
  
 接下來，覆寫 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> 方法以序列化物件。  在傳送傳出訊息之前會呼叫這個方法。  
  
 如果要將自訂格式器插入服務應用程式中，請使用作業行為將 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 物件指派給 <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> 屬性。  如需行為的資訊，請參閱[使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>   
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>   
 [使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)