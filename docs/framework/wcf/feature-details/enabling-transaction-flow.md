---
title: "啟用異動流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 814df9ff4fb11b0aa59270ac251b5dbd9ed7fe96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-transaction-flow"></a>啟用異動流程
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供靈活自如的選項，可控制交易流程。 服務的交易流程設定可以使用屬性和組態的組合來表示。  
  
## <a name="transaction-flow-settings"></a>異動流程設定  
 異動流程設定是針對服務端點所產生的設定，而且是下列三個值交集的結果：  
  
-   針對服務合約中每個方法所指定的 <xref:System.ServiceModel.TransactionFlowAttribute> 屬性。  
  
-   特定繫結中的 `TransactionFlow` 繫結屬性。  
  
-   特定繫結中的 `TransactionFlowProtocol` 繫結屬性。 `TransactionFlowProtocol` 繫結屬性可讓您選擇使用兩種可用來流動交易的不同交易通訊協定， 下列章節會簡要說明其中的每一種。  
  
### <a name="ws-atomictransaction-protocol"></a>WS-AtomicTransaction 通訊協定  
 WS-AtomicTransaction (WS-AT) 通訊協定在需要可與協力廠商堆疊互通的案例中很有用。  
  
### <a name="oletransactions-protocol"></a>OleTransactions 通訊協定  
 在不需要可與協力廠商通訊協定堆疊互通，服務的部署者事先知道 WS-AT 通訊協定已於本機上停用，或是現有的網路拓撲不利於使用 WS-AT 等案例中，OleTransactions 通訊協定都會非常有用。  
  
 下表顯示可以使用這些不同組合產生的不同交易流程類型。  
  
|TransactionFlow<br /><br /> 繫結|TransactionFlow 繫結屬性|TransactionFlowProtocol 繫結通訊協定|交易流程的類型|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|強制性|true|WS-AT|異動必須以可互通的 WS-AT 格式來流動。|  
|強制|true|OleTransactions|交易必須以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions 格式來流動。|  
|強制|False|不適用|由於不是有效的組態而不適用。|  
|Allowed|true|WS-AT|異動可以用可互通的 WS-AT 格式來流動。|  
|Allowed|true|OleTransactions|交易可以用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions 格式來流動。|  
|Allowed|False|任何值|未流動交易。|  
|NotAllowed|任何值|任何值|未流動異動。|  
  
 下表摘要說明訊息處理的結果。  
  
|傳入訊息|異動流程設定|交易標頭|訊息處理結果|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|異動符合預期的通訊協定格式|Allowed 或 Mandatory|`MustUnderstand`等於 `true`。|處理序|  
|異動不符合預期的通訊協定格式|強制|`MustUnderstand`等於 `false`。|由於需要異動而被拒絕|  
|交易不符合預期的通訊協定格式|Allowed|`MustUnderstand`等於 `false`。|由於不瞭解標頭而被拒絕|  
|使用任何通訊協定格式的交易|NotAllowed|`MustUnderstand`等於 `false`。|由於不瞭解標頭而被拒絕|  
|無交易|強制|N/A|由於需要交易而被拒絕|  
|無異動|Allowed|N/A|處理序|  
|無異動|NotAllowed|N/A|處理序|  
  
 雖然合約中的每個方法可能都有不同的交易流程需求，但是交易流程通訊協定設定的範圍是位於繫結層級。 這表示端點相同 (繫結程序因而相同) 的所有方法也有相同的原則允許或要求異動流程，而且這些方法在可行的情況下擁有相同的異動通訊協定。  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>啟用方法層級上的異動流程  
 在服務合約中的所有方法不一定有相同的異動流程需求。 因此，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會提供屬性架構機制，以便呈現每一種方法的交易流程偏好設定。 指定服務作業接受交易標頭時所位於之層級的 <xref:System.ServiceModel.TransactionFlowAttribute> 會完成這項動作。 若要啟用交易流程，您應該要使用這個屬性來標記您的服務合約方法。 這個屬性會接受其中一個 <xref:System.ServiceModel.TransactionFlowOption> 列舉值，其預設值為 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。 如果已指定 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> 以外的任何值，即表示此方法一定不能是單向方法。 開發人員可以使用這個屬性來指定方法層級的交易流程需求，或是設計階段的條件約束。  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>啟用端點層級上的異動流程  
 除了 <xref:System.ServiceModel.TransactionFlowAttribute> 屬性所提供的方法層級交易流程設定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 還會提供交易流程的端點設定，可讓系統管理員控制更高層級的交易流程。  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 會完成這個動作，它可讓您在端點的繫結設定中啟用或停用傳入交易流程，並且指定傳入交易的所需交易通訊協定格式。  
  
 如果該繫結已停用交易流程，但是服務合約上的其中一個作業需要傳入交易，則會在服務啟動時擲回驗證例外狀況。  
  
 大多數由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的標準繫結都會包含 `transactionFlow` 和 `transactionProtocol` 屬性，可讓您將特定的繫結設定為接受傳入交易。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]設定組態項目，請參閱[\<繫結 >](../../../../docs/framework/misc/binding.md)。  
  
 系統管理員或部署者都可以透過組態檔，在部署時使用端點層級異動流程來設定異動流程需求或條件約束。  
  
## <a name="security"></a>安全性  
 為了確保系統的安全性和完整性，將異動在應用程式之間流動時，必須要保護訊息交換的安全。 您不應該將異動細節流動或公開到沒有資格參與相同異動的任何應用程式。  
  
 當透過使用中繼資料交換，在未知或未受信任的 Web 服務上產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端時，對於這些 Web 服務作業的呼叫應該要盡可能地隱藏目前的交易。 下列範例示範如何進行這項操作。  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 此外，服務應該設定為只接受其已驗證和授權之用戶端的傳入交易。 只有在傳入交易來自受到高度信任的用戶端時，才應該接受這些交易。  
  
## <a name="policy-assertions"></a>原則判斷提示  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用原則判斷提示來控制交易流程。 原則判斷提示可以在服務的原則文件中找到，該文件是由合約、組態及屬性彙總而成。 用戶端可以使用 HTTP GET 或 WS-MetadataExchange 要求-回覆來取得服務的原則文件。 用戶端可以接著處理該原則文件，判斷在服務合約中的哪些作業可支援或需要異動流程。  
  
 交易流程原則判斷提示會指定用戶端應該傳送到服務以代表交易的 SOAP 標頭，藉此變動交易流程。 所有交易標頭都必須標記為 `MustUnderstand` 等於 `true`。 任何不是這樣標記的訊息都會被拒絕，並且產生 SOAP 錯誤。  
  
 單一作業中只能存在一個與交易相關的原則判斷提示。 作業若是包含一個以上的交易判斷提示，該原則文件就會被視為無效，而且會被 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拒絕。 此外，每個連接埠類型內部只能存在單一異動通訊協定。 與作業-參考一個以上的交易通訊協定的單一連接埠類型內部的原則文件會被視為無效，而且將會拒絕的[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 輸出訊息或是單向輸入訊息如果存在異動判斷提示，該原則文件就會被視為無效。
