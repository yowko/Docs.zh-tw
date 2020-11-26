---
title: ServiceModel 交易組態
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 27deaf38a8809b8a7fca560cc6783bd24dc43686
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242886"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel 交易組態

Windows Communication Foundation (WCF) 提供三個屬性來設定服務的交易： `transactionFlow` 、 `transactionProtocol` 和 `transactionTimeout` 。  
  
## <a name="configuring-transactionflow"></a>設定 transactionFlow  

 WCF 提供的大部分預先定義系 `transactionFlow` `transactionProtocol` 結都會包含和屬性，讓您可以設定系結，以接受使用特定交易流程通訊協定之特定端點的傳入交易。 此外，您可以使用 `transactionFlow` 元素及其 `transactionProtocol` 屬性來建置您自訂的繫結。 如需設定設定元素的詳細資訊，請參閱 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 和 [WCF 設定架構](../../configure-apps/file-schema/wcf/index.md)。  
  
 `transactionFlow` 屬性會指定是否要為使用繫結的服務端點啟用交易流程。  
  
## <a name="configuring-transactionprotocol"></a>設定 transactionProtocol  

 `transactionProtocol` 屬性會指定交易通訊協定與使用繫結的服務端點一起使用。  
  
 以下是組態區段的範例，其中設定了支援異動流程的指定繫結程序，以及使用 WS-AtomicTransaction 通訊協定的範例。  
  
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

 您可以 `transactionTimeout` 在設定檔的元素中，設定 WCF 服務的屬性 `behavior` 。 下列程式碼會示範如何執行此項作業。  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` 屬性會指定在服務所建立之新交易必須完成的時間週期。 這個屬性可當做任何建立新異動之作業的 <xref:System.Transactions.TransactionScope> 逾時使用，若套用了 <xref:System.ServiceModel.OperationBehaviorAttribute>，則 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性會設為 `true`。  
  
 逾時會指定從建立異動到完成兩階段異動認可通訊協定中的階段 1 的時間範圍。  
  
 如果在 `service` 組態區段中設定這個屬性，您至少應該以 <xref:System.ServiceModel.OperationBehaviorAttribute> 套用一個對應服務的方法，其中 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性設定為 `true`。  
  
 請注意，所使用的逾時值會是這個 `transactionTimeout` 組態設定和任何 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 屬性間的較小值。  
  
## <a name="see-also"></a>另請參閱

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [WCF 設定架構](../../configure-apps/file-schema/wcf/index.md)
