---
title: "HOW TO：在服務合約中宣告錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# HOW TO：在服務合約中宣告錯誤
在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。  不過在 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式中，藉由在服務合約中宣告 SOAP 錯誤，服務合約便可指定傳回用戶端的錯誤資訊。  如需例外狀況和錯誤之間的關係概觀，請參閱[指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。  
  
### 建立會指定 SOAP 錯誤的服務合約  
  
1.  建立其中至少包含一個作業的服務合約。  如需範例，請參閱 [HOW TO：定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。  
  
2.  選取作業，這個作業會指定用戶端預期會收到通知的錯誤狀況。  若要決定確實將 SOAP 錯誤傳回用戶端的錯誤狀況，請參閱[指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。  
  
3.  將 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName> 套用至選取的作業，並將可序列化的錯誤類型傳遞至建構函式。  如需建立及使用可序列化類型的詳細資訊，請參閱[指定服務合約中的資料傳輸](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。  下列範例將示範如何指定會在 `GreetingFault` 中產生 `SampleMethod` 作業。  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  對合約中會與用戶端溝通錯誤狀況的所有作業，重複步驟 2 和 3。  
  
## 實作作業以傳回指定的 SOAP 錯誤  
 一旦作業已指定可傳回特定 SOAP 錯誤 \(如之前的程序所示\)，以與呼叫應用程式溝通錯誤狀況，則下一個步驟就是實作該指定項目。  
  
#### 在作業中擲回指定的 SOAP 錯誤  
  
1.  在作業中發生 <xref:System.ServiceModel.FaultContractAttribute> 特定的錯誤狀況時，會擲回新的 <xref:System.ServiceModel.FaultException%601?displayProperty=fullName>，其中指定的 SOAP 錯誤為型別參數。  下列範例會示範如何在之前程序中顯示的 `SampleMethod` 中擲回 `GreetingFault`，以及如何在下列「程式碼」區段中擲回。  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## 範例  
 下列程式碼範例會顯示對 `SampleMethod` 作業指定 `GreetingFault` 的單一作業實作。  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## 請參閱  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName>   
 <xref:System.ServiceModel.FaultException%601?displayProperty=fullName>