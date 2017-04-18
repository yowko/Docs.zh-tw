---
title: "HOW TO：使用通道處理站以非同步方式呼叫作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：使用通道處理站以非同步方式呼叫作業
本主題涵蓋用戶端如何能夠在使用 <xref:System.ServiceModel.ChannelFactory%601> 架構的用戶端應用程式時，非同步地存取服務作業   \(當使用 <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> 物件來叫用服務時，您可以使用事件驅動的非同步呼叫模型。  如需詳細資訊，請參閱[HOW TO：以非同步方式呼叫 WCF 服務作業](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。  如需事件架構的非同步呼叫模型的詳細資訊，請參閱[Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)\)。  
  
 本主題中的服務會實作 `ICalculator` 介面。  用戶端可透過非同步的方式來呼叫在此介面上的作業，這表示類似 `Add` 的作業會分割為兩個方法，`BeginAdd` 和 `EndAdd`，其中前者會啟始呼叫，後者則會在作業完成時擷取結果。  如需示範如何在服務中以非同步方式來實作作業的範例，請參閱 [HOW TO：實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。  如需同步與非同步作業的詳細資料，請參閱[同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。  
  
## 程序  
  
#### 若要以非同步方式呼叫 WCF 服務作業  
  
1.  配合 `/async` 選項來執行 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，如下列命令所示。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
  
    ```  
  
     這會針對作業的服務合約產生非同步用戶端版本。  
  
2.  建立要在非同步作業完成時呼叫的回呼函式 \(Callback Function\)，如下列範例程式碼所示。  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  若要以非同步方式來存取服務作業，請建立用戶端和呼叫 `Begin[Operation]` \(例如，`BeginAdd`\)，並指定回呼函式，如下列範例程式碼所示。  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     當此回呼函式執行時，用戶端便會呼叫 `End<operation>` \(例如，`EndAdd`\) 以擷取結果。  
  
## 範例  
 在用於上述程序中之用戶端程式碼所使用的服務會實作 `ICalculator` 介面，如下列程式碼所示。  在服務端，合約的 `Add` 和 `Subtract` 作業會由 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 執行階段同步叫用，即使已經在用戶端上非同步叫用了先前的用戶端步驟也是一樣。  在服務端，會使用 `Multiply` 和 `Divide` 作業來非同步叫用服務，即使用戶端會同步叫用這些服務也是一樣。  這個範例會將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`。  這項屬性設定在配合 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 非同步模式 \(Asynchronous Pattern\) 的實作時，便會告知執行階段以非同步方式來叫用作業。  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## 請參閱  
 [Service Contract: Asynchronous Sample](http://msdn.microsoft.com/zh-tw/833db946-f511-4f64-a26f-2759a11217c7)