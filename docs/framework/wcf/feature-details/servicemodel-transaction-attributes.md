---
title: ServiceModel 異動屬性
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: 79d97eee328d816281348b5b15cf779e1ee65893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="servicemodel-transaction-attributes"></a>ServiceModel 異動屬性
Windows Communication Foundation (WCF) 提供三個標準屬性<xref:System.ServiceModel>屬性，可讓您設定的 WCF 服務異動行為：  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> 屬性指定服務合約中的作業是否願意接受來自用戶端的傳入交易。 屬性 (Attribute) 使用下列屬性 (Property) 提供這項控制：交易使用 <xref:System.ServiceModel.TransactionFlowOption> 列舉以指定傳入交易是否為 <xref:System.ServiceModel.TransactionFlowOption.Mandatory>、<xref:System.ServiceModel.TransactionFlowOption.Allowed> 或 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。  
  
 這是唯一將服務作業與外部用戶端互動產生關聯的屬性。 下列章節中描述的屬性與使用執行作業內的交易有關。  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性指定服務合約實作的內部執行行為。 這個屬性 (Attribute) 的交易特定屬性 (Property) 包括：  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> 指定當工作階段關閉時是否會完成未完成的交易。 這個屬性的預設值為 `false`。 如果這個屬性是 `true`，並且傳入工作階段依正常程序關閉，而不是因為網路或用戶端錯誤導致關閉，則任何未完成的交易都會成功完成。 否則，如果這個屬性是 `false`，或是如果工作階段不是依正常程序關閉，則當工作階段關閉時就會復原未完成的交易。 如果這個屬性是 `true`，則傳入通道必須是以工作階段為依據。  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> 指定當交易完成時是否要釋放基礎服務執行個體。 這個屬性的預設值為 `true`。 下一個傳入訊息會導致建立新的基礎執行個體，並捨棄之前執行個體可能持有的任何每個交易狀態。 釋放服務執行個體是服務執行的內部動作，並且不會影響用戶端可能已建立的任何現有連線或工作階段。 這個功能等同於 COM+ 提供的 Just-in-Time 啟動功能。 如果屬性是 `true`，則 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 必須等於 <xref:System.ServiceModel.ConcurrencyMode.Single>。 否則，在啟動期間服務會發生無效組態驗證例外狀況。  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 指定服務內交易所使用的隔離等級，這個屬性會使用其中一個 <xref:System.Transactions.IsolationLevel> 值。 如果本機隔離等級屬性不是 <xref:System.Transactions.IsolationLevel.Unspecified>，則傳入交易的隔離等級必須符合此本機屬性的設定。 否則，就會拒絕傳入異動並且將錯誤傳回用戶端。 如果 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 是 `true`，並且沒有流動的交易，這個屬性會判定在本機建立之交易要使用的 <xref:System.Transactions.IsolationLevel> 值。 如果<xref:System.Transactions.IsolationLevel>設<xref:System.Transactions.IsolationLevel.Unspecified>， <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable>用。  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 指定在服務所建立之新交易必須完成的時間間隔。 如果達到這個時間而交易尚未完成的話，交易就會中止。 <xref:System.TimeSpan> 會用來當做將 <xref:System.Transactions.TransactionScope> 設定為 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 之任何作業，以及建立新交易的 `true` 逾時。 從建立交易到完成兩階段交易認可通訊協定中的階段 1，所允許的逾時期間上限。 所使用的逾時值永遠都是 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 屬性和 `transactionTimeout` 組態設定之間較低的值。  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性指定服務實作中方法的行為。 您可以用來表示作業的特定執行行為。 這個屬性的屬性不會影響服務合約的 Web 服務描述語言 (WSDL) 描述，而且是單純的元素 WCF 程式設計模型可讓開發人員必須自行實作的通用功能。  
  
 這個屬性 (Attribute) 有下列異動特定屬性 (Property)：  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 指定方法是否必須在現用交易的範圍內執行。 預設值為 `false`。 如果沒有為方法設定 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性，這也表示該方法不會在交易中執行。 如果作業不需要交易範圍，則存在於訊息標頭中的任何交易都不會啟動，而且保持為 <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> 的 <xref:System.ServiceModel.OperationContext> 項目。 如果作業需要異動範圍，則異動來源會衍生自下列其中一個：  
  
    -   如果交易從用戶端流入，則會在使用分散式交易建立的交易範圍內執行方法。  
  
    -   使用已佇列的傳輸時，會使用用來清除佇列訊息的交易。 請注意，使用的交易並不是流動交易，因為不是由訊息的原始傳送者提供。  
  
    -   自訂傳輸可以透過使用 `TransportTransactionProperty` 提供交易。  
  
    -   如果上述都無法提供交易的外部來源，就會在呼叫方法之前立即建立新的 <xref:System.Transactions.Transaction> 執行個體。  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 指定如果沒有發生未處理的例外狀況，方法執行的交易是否會自動完成。 如果這個屬性是 `true`，當使用者方法在傳回時沒有發生例外狀況時，呼叫基礎結構會自動將交易標記為「已完成」。 如果這個屬性是 `false`，則交易會附加至執行個體，並且只有在用戶端呼叫使用這個屬性標記為 `true` 的後續方法，或是如果後續方法明確地呼叫 <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 時，才會標記為「已完成」。 除非 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> 屬性設定為 `true`，否則無法在從未標記為「已完成」的交易中執行這些結果，並且也不會認可其中包含的工作。 如果這個屬性設定為 `true`，您必須搭配工作階段使用通道，並且 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 必須設定為 <xref:System.ServiceModel.InstanceContextMode.PerSession>。
