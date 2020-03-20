---
title: ServiceModel 交易組態
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184458"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel 交易組態
Windows 通信基礎 （WCF） 提供了三個屬性來佈建服務的事務`transactionFlow`：`transactionProtocol`和`transactionTimeout`。  
  
## <a name="configuring-transactionflow"></a>設定 transactionFlow  
 WCF 提供的大多數預定義的綁定都包含`transactionFlow`和`transactionProtocol`屬性，以便可以將綁定配置為使用特定的事務流協定接受特定終結點的傳入事務。 此外，您可以使用 `transactionFlow` 元素及其 `transactionProtocol` 屬性來建置您自訂的繫結。 有關設置配置元素的詳細資訊，請參閱[\<綁定>](../../configure-apps/file-schema/wcf/bindings.md)和[WCF 配置架構](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)。  
  
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
 您可以在設定檔`behavior`的元素中`transactionTimeout`配置 WCF 服務的屬性。 下列程式碼會示範如何執行此項作業。  
  
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

- [\<綁定>](../../configure-apps/file-schema/wcf/bindings.md)
- [WCF 配置架構](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
