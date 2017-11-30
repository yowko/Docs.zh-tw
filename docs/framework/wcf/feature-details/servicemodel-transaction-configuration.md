---
title: "ServiceModel 異動組態"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54b07eff0b54816fe2d359a27f75b07ecb9f355a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel 異動組態
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供了三個屬性，可用於設定服務的交易：`transactionFlow`、`transactionProtocol` 和 `transactionTimeout`。  
  
## <a name="configuring-transactionflow"></a>設定 transactionFlow  
 大部分所提供預先定義的繫結 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會包含 `transactionFlow` 和 `transactionProtocol` 屬性，因此您可以將繫結設定為接受使用特定交易流程通訊協定之特定端點的傳入交易。 此外，您可以使用 `transactionFlow` 元素及其 `transactionProtocol` 屬性來建置您自訂的繫結。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]設定組態項目，請參閱[\<繫結 >](../../../../docs/framework/misc/binding.md)和[WCF 組態結構描述](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)。  
  
 `transactionFlow` 屬性會指定是否要為使用繫結的服務端點啟用交易流程。  
  
## <a name="configuring-transactionprotocol"></a>設定 transactionProtocol  
 `transactionProtocol` 屬性會指定交易通訊協定與使用繫結的服務端點一起使用。  
  
 以下是組態區段的範例，其中設定了支援交易流程的指定繫結，以及使用 WS-AtomicTransaction 通訊協定的範例。  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"   
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"   
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>設定 transactionTimeout  
 您可以在組態檔的 `transactionTimeout` 項目內為您的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務設定 `behavior` 屬性。 下列程式碼會示範如何執行此項作業。  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` 屬性會指定在服務所建立之新交易必須完成的時間週期。 這個屬性可當做任何建立新交易之作業的 <xref:System.Transactions.TransactionScope> 逾時使用，若套用了 <xref:System.ServiceModel.OperationBehaviorAttribute>，則 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性會設為 `true`。  
  
 逾時會指定從建立交易到完成兩階段交易認可通訊協定中的階段 1 的時間範圍。  
  
 如果在 `service` 組態區段中設定這個屬性，您至少應該以 <xref:System.ServiceModel.OperationBehaviorAttribute> 套用一個對應服務的方法，其中 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性設定為 `true`。  
  
 請注意，所使用的逾時值會是這個 `transactionTimeout` 組態設定和任何 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 屬性間的較小值。  
  
## <a name="see-also"></a>另請參閱  
 [\<繫結 >](../../../../docs/framework/misc/binding.md)  
 [WCF 組態結構描述](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
