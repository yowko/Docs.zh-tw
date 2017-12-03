---
title: "錯誤處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215fb30772e4f1b25e20303b3f83d6fe0c00ebae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling"></a>錯誤處理
## <a name="error-handling-in-windows-communication-foundation"></a>Windows Communication Foundation 的錯誤處理  
 當服務發生未預期的例外狀況或錯誤時，有幾種方式可設計例外狀況處理方案。 雖然沒有單一 「 正確 」 或 「 最佳做法 」 的錯誤處理方案，可以考慮多重有效路徑。 通常建議實作混合式解決方案，結合多個方法，從清單下，根據 WCF 實作的型別和例外狀況，處理的頻率的複雜度與未處理性質例外狀況，以及任何相關聯的追蹤、 記錄或原則需求。  
  
 這些方案在本節的其他部分會做更深入的說明。  
  
### <a name="the-microsoft-enterprise-library"></a>Microsoft 企業程式庫  
 Microsoft 企業程式庫例外狀況處理應用程式區塊協助實作常見的設計模式，並建立一致策略以處理企業應用程式的所有架構圖層中發生的例外狀況。 其設計目的為支援包含在應用程式元件之 catch 陳述式的典型程式碼。 並非在同一應用程式的相同 catch 區塊重複此程式碼 (例如記錄例外狀況資訊的程式碼)，例外狀況處理應用程式區塊可讓開發人員封裝這個邏輯，做為可重複使用的例外狀況處理常式。  
  
 這個程式庫包含隨附的錯誤合約例外狀況處理常式。 這個例外狀況處理常式設計使用於 Windows® Communication Foundation (WCF) 服務界限，並產生例外狀況的新錯誤合約。  
  
 應用程式區塊的目標是納入常用的最佳做法，並在您的應用程式中提供處理例外狀況的常見方法。 另一方面，自訂錯誤處理常式和自行開發錯誤合約也非常有用。 例如，自訂錯誤處理常式提供一個好機會，可自動升級所有 FaultExceptions 的例外，將記錄功能加入至您的應用程式。  
  
 如需詳細資訊，請參閱[Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff632023.aspx)。  
  
### <a name="dealing-with-expected-exceptions"></a>處理預期的例外狀況。  
 採取適當的動作會攔截預期的例外狀況，每個作業或相關擴充點，決定是否它們，可以復原，並傳回適當的自訂錯誤 FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>使用 IErrorHandler 處理未預期的例外狀況。  
 若要處理的非預期的例外狀況，建議的採取就是動作的 「 攔截 」 IErrorHandler。 在 WCF 執行階段層級 （「 服務模型 」 層），而不是通道層的錯誤處理常式只會攔截例外狀況。 在通道層級攔截 IErrorHandler 的唯一方式是建立自訂通道，在大部分的情況下不建議使用。  
  
 「 非預期例外狀況 」 通常是處理的例外狀況，都無法復原的例外狀況是，相反地，未預期的使用者例外狀況。 無法修復的例外狀況 （例如記憶體不足例外狀況） – 其中一個通常由[服務模型例外狀況處理常式](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx)自動 – 無法通常可正常地處理，並處理這類例外狀況的唯一理由可能是完全做其他記錄或傳回給用戶端的標準例外狀況。 處理中的例外狀況發生於訊息的處理過程中 - 例如序列化、編碼器或格式器層級 - 通常無法在 IErrorHandler 處理，因為對錯誤處理常式而言，這些例外狀況發生的時間通常太早或太晚，使其無法介入。 同樣地，也無法在 IErrorHandler 處理傳輸例外狀況。  
  
 當例外狀況擲回時，您可使用 IErrorHandler 明確控制應用程式的行為。 您可以：  
  
1.  決定是否要傳送錯誤給用戶端。  
  
2.  以錯誤取代例外狀況。  
  
3.  以另一個錯誤取代錯誤  
  
4.  執行記錄或追蹤  
  
5.  執行其他自訂活動  
  
 針對您的服務將錯誤處理常式加入通道發送器的 ErrorHandlers 屬性，即可安裝自訂錯誤處理常式。  錯誤處理常式可能不只一個，會依照它們加入集合的順序呼叫它們。  
  
 IErrorHandler.ProvideFault 可控制傳送至用戶端的錯誤訊息。 不論服務中的作業擲回何種例外狀況類型，都會呼叫這個方法。 如果此處沒有執行任何作業，WCF 會採用其預設行為並繼續進行，如同自訂錯誤處理常式並不存在一樣。  
  
 您可能使用此方法的情況如下，當您想在例外狀況傳送給用戶端前，建立一個集中位置以將例外狀況轉換為錯誤時 (確保不會處理執行個體，且不會將通道移至錯誤狀態)。  
  
 IErrorHandler.HandleError 方法通常用來實作與錯誤相關的行為，例如錯誤記錄，系統通知及關閉應用程式等。可在服務內的多個地方呼叫 IErrorHandler.HandleError，根據錯誤擲回的地方，充當作業的同一個執行緒不一定會呼叫 HandleError 方法，這一點無法保證。  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>處理 WCF 外的例外狀況。  
 通常，組態例外狀況、資料庫連接字串例外狀況以及其他類似的例外狀況，都可能發生在 WCF 應用程式的內容中，但其本身並不是由服務模型或 Web 服務自己所造成的例外狀況。 這些例外狀況的 web 服務的外部 「 一般 」 例外狀況，並應該比照環境中的其他外部例外狀況的處理。  
  
### <a name="tracing-exceptions"></a>追蹤例外狀況  
 追蹤是其中一個可能會看到所有例外狀況的只有 「 包羅萬象 」 位置。 如需追蹤和記錄例外狀況的詳細資訊，請參閱追蹤和記錄。  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>使用 WebGetAttribute 和 WebInvokeAttribute 時，URI 範本發生錯誤。  
 WebGet 和 WebInvoke 屬性允許您指定 URI 範本，此範本可將要求位址的元件對應至作業參數。 例如，URI 範本 "weather/{state}/{city}" 將要求位址對應到常值語彙基元、參數具名國家/地區和參數具名城市。 接著這些參數可能依名稱繫結至一些作業的型式參數。  
  
 當類型合約的型式參數可能為非字串類型時，範本參數在 URI 中會以字串形式出現。 因此需要在作業可叫用之前進行轉換。 A[轉換格式資料表](http://msdn.microsoft.com/library/bb412172.aspx)可用。  
  
 不過，如果轉換失敗，則無法讓作業知道錯誤已發生。 類型轉換改以分派失敗的形式呈現。  
  
 如同許多其他類型的分派失敗一般，透過安裝錯誤處理常式也可以檢查類型轉換分派失敗。 呼叫 IErrorHandler 擴充點，以處理服務層級例外狀況。 從此處，也可以選擇要送回呼叫端的回應 - 同時也執行任何自訂的工作和報告。  
  
## <a name="see-also"></a>另請參閱  
 [基本 WCF 錯誤處理](http://msdn.microsoft.com/library/gg281715.aspx)
