---
title: 指定用戶端執行階段行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f750978eaa617a5505bb27a1535797320a76b0d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164368"
---
# <a name="specifying-client-run-time-behavior"></a>指定用戶端執行階段行為
Windows Communication Foundation (WCF) 用戶端，例如 Windows Communication Foundation (WCF) 服務，可以設定以修改以符合用戶端應用程式的執行階段行為。 指定用戶端執行階段行為時有三個屬性可供使用。 雙工用戶端回呼物件可以使用 <xref:System.ServiceModel.CallbackBehaviorAttribute> 和 <xref:System.ServiceModel.Description.CallbackDebugBehavior> 屬性來修改其執行階段行為。 而另一個屬性 <xref:System.ServiceModel.Description.ClientViaBehavior> 則可用來區隔邏輯目的和立即網路目的。 此外，雙工用戶端回呼類型也可使用一些服務端的行為。 如需詳細資訊，請參閱 <<c0> [ 指定服務執行階段行為](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)。  
  
## <a name="using-the-callbackbehaviorattribute"></a>使用 CallbackBehaviorAttribute  
 您可以使用 <xref:System.ServiceModel.CallbackBehaviorAttribute> 類別，即可設定或擴充用戶端應用程式中回呼合約實作的執行行為。 這個屬性對回呼類別執行的函式類似於 <xref:System.ServiceModel.ServiceBehaviorAttribute> 類別，而執行個體化行為和交易設定則為其例外。  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> 類別必須套用至實作回呼合約的類別。 如果套用至非雙工合約實作，便會在執行階段擲回 <xref:System.InvalidOperationException> 例外狀況 (Exception)。 下列程式碼範例會顯示回呼物件上的 <xref:System.ServiceModel.CallbackBehaviorAttribute> 類別，這個類別會使用 <xref:System.Threading.SynchronizationContext> 物件來判斷要封送處理的執行緒、使用 <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> 屬性以強制執行訊息驗證，並使用 <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> 屬性將例外狀況當做 <xref:System.ServiceModel.FaultException> 物件傳回服務以進行偵錯。  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>使用 CallbackDebugBehavior 啟用 Managed 例外狀況資訊的流動  
 如果您以程式設計方式或從應用程式組態檔將 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性設定為 `true`，則可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。  
  
 將 Managed 例外狀況資訊傳回服務可能導致安全性風險，因為例外狀況詳細資料會公開未授權的服務可使用的內部用戶端實作相關資訊。 此外，雖然也能以程式設計方式設定 <xref:System.ServiceModel.Description.CallbackDebugBehavior> 屬性，不過在部署時很容易會忘記停用 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>。  
  
 由於牽涉到安全性議題，我們強烈建議您：  
  
-   使用應用程式的組態檔將 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> 屬性的值設定為 `true`。  
  
-   您只能在受控制的偵錯狀況下這樣做。  
  
 下列程式碼範例示範的用戶端會指示 WCF 在傳回 managed 例外狀況資訊從用戶端回呼物件的 SOAP 訊息中的組態檔。  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>使用 ClientViaBehavior 行為  
 您可以使用 <xref:System.ServiceModel.Description.ClientViaBehavior> 行為，對應該建立的傳輸通道指定統一資源識別項。 當立即網路目的不是訊息的預期處理器時，請使用這個行為。 當呼叫應用程式不需要知道最終目的，或者目的 `Via` 標頭不是位址時，這個行為可啟用多重躍點交談。  
  
## <a name="see-also"></a>另請參閱

- [指定服務執行階段行為](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
