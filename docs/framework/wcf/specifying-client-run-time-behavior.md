---
title: "指定用戶端執行階段行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "行為 [WCF] 時，系統提供的用戶端"
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 指定用戶端執行階段行為
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 用戶端就如同 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務，可以在設定之後修改執行階段行為，以配合用戶端應用程式。 指定用戶端執行階段行為時有三個屬性可供使用。 雙工用戶端回呼物件可以使用<xref:System.ServiceModel.CallbackBehaviorAttribute>和<xref:System.ServiceModel.Description.CallbackDebugBehavior>屬性來修改其執行階段行為。 而另一個屬性<xref:System.ServiceModel.Description.ClientViaBehavior>，可用來區隔邏輯目的和立即網路目的。 此外，雙工用戶端回呼類型也可使用一些服務端的行為。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][指定服務執行階段行為](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)。  
  
## <a name="using-the-callbackbehaviorattribute"></a>使用 CallbackBehaviorAttribute  
 您可以設定或擴充用戶端應用程式中回呼合約實作的執行行為使用<xref:System.ServiceModel.CallbackBehaviorAttribute>類別。 這個屬性對回呼類別，做為執行類似的功能<xref:System.ServiceModel.ServiceBehaviorAttribute>類別，除了執行個體化行為和交易設定。  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>類別必須套用至實作回呼合約的類別。 如果套用至雙工合約實作， <xref:System.InvalidOperationException>在執行階段擲回例外狀況。 下列程式碼範例顯示<xref:System.ServiceModel.CallbackBehaviorAttribute>類別上使用的回呼物件<xref:System.Threading.SynchronizationContext>物件判斷要封送處理，執行緒<xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A>屬性以強制執行訊息驗證和<xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A>屬性以傳回例外狀況當做<xref:System.ServiceModel.FaultException>服務以進行偵錯的物件。  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>使用 CallbackDebugBehavior 啟用 Managed 例外狀況資訊的流動  
 您可以讓 managed 的例外狀況資訊傳回給服務以進行偵錯設定的用戶端回呼物件中流動<xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>屬性`true`以程式設計方式或從應用程式組態檔。  
  
 將 Managed 例外狀況資訊傳回服務可能導致安全性風險，因為例外狀況詳細資料會公開未授權的服務可使用的內部用戶端實作相關資訊。 此外，雖然<xref:System.ServiceModel.Description.CallbackDebugBehavior>屬性也以程式設計方式設定時，很容易會忘記停用<xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>部署時。  
  
 由於牽涉到安全性議題，我們強烈建議您：  
  
-   您可以使用應用程式組態檔設定的值<xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>屬性`true`。  
  
-   您只能在受控制的偵錯狀況下這樣做。  
  
 下列程式碼範例所示範的用戶端組態檔，會指示 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 從 SOAP 訊息中的用戶端回呼物件中傳回 Managed 例外狀況資訊。  
  
 [!code[SCA.CallbackContract#4](../../../samples/snippets/common/VS_Snippets_CFX/sca.callbackcontract/common/client.exe.config#4)]
 [!code-csharp[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]
 [!code-vb[SCA.CallbackContract#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.callbackcontract/vb/client.exe.config#4)]  
  
## <a name="using-the-clientviabehavior-behavior"></a>使用 ClientViaBehavior 行為  
 您可以使用<xref:System.ServiceModel.Description.ClientViaBehavior>行為，以指定應建立傳輸通道的統一資源識別項。 當立即網路目的不是訊息的預期處理器時，請使用這個行為。 當呼叫應用程式不需要知道最終目的，或者目的 `Via` 標頭不是位址時，這個行為可啟用多重躍點交談。  
  
## <a name="see-also"></a>另請參閱  
 [指定服務執行階段行為](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)