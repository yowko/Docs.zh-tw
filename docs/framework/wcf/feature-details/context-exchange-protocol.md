---
title: 內容交換通訊協定
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a6bc0ac45282d94a6aea8dbbdb5a7d34163c692e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216999"
---
# <a name="context-exchange-protocol"></a>內容交換通訊協定
本節說明 Windows Communication Foundation (WCF) 版本.NET Framework 3.5 版中導入的內容交換通訊協定。 這項通訊協定可讓用戶端通道接受服務所提供的內容，並透過相同的用戶端通道執行個體將之套用到該服務的後續所有要求。 內容交換通訊協定的實作可以使用下列兩個機制其中之一來傳播內容伺服器與用戶端之間：HTTP cookie 或 SOAP 標頭。  
  
 內容交換通訊協定可在自訂通道層中實作。 通道會透過 <xref:System.ServiceModel.Channels.ContextMessageProperty> 屬性，在應用程式層來回傳送內容。 至於端點之間的傳輸，內容值將在通道層上序列化為 SOAP 標頭，或是在代表 HTTP 要求和回應的訊息屬性之間來回轉換。 在第二個情況中，我們預期其中一個基礎通道層會將 HTTP 要求和回應訊息屬性個別轉換至 HTTP Cookie，反之亦然。 您可透過 <xref:System.ServiceModel.Channels.ContextExchangeMechanism> 上的 <xref:System.ServiceModel.Channels.ContextBindingElement> 屬性，選擇用來交換內容的機制。 有效值為 `HttpCookie` 或 `SoapHeader`。  
  
 在用戶端上，通道的執行個體可以依據通道屬性 <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> 上的設定，以兩種模式來運作。  
  
## <a name="mode-1-channel-context-management"></a>模式 1:通道內容管理  
 當 <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> 設定為 `true` 時，這就是預設的模式。 在此模式中，內容通道會管理內容，並在其存留期間快取內容。 您可以呼叫 `IContextManager` 方法，透過通道屬性 `GetContext` 從通道擷取內容。 您也可以呼叫通道屬性上的 `SetContext` 方法，在開啟通道之前，使用特定內容預先初始化通道。 一旦通道透過內容初始化完畢，就無法重設。  
  
 下列為此模式中的不變量清單：  
  
-   在通道已經開啟的情況下，任何使用 `SetContext` 來重設內容的嘗試都會擲回 <xref:System.InvalidOperationException>。  
  
-   在傳出的訊息中使用 <xref:System.ServiceModel.Channels.ContextMessageProperty> 來傳送內容的嘗試都會擲回 <xref:System.InvalidOperationException>。  
  
-   如果在通道已經使用特定內容初始化之後，從伺服器接收包含特定內容的訊息時就會產生 <xref:System.ServiceModel.ProtocolException>。  
  
    > [!NOTE]
    >  只有當開啟的通道未明確設定任何內容時，才適合從伺服器接收初始內容。  
  
-   傳入訊息上的 <xref:System.ServiceModel.Channels.ContextMessageProperty> 一律為 null。  
  
## <a name="mode-2-application-context-management"></a>模式 2:應用程式內容管理  
 當 <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> 設為 `false` 的時候，會變成這個模式。 在此模式中，內容通道不會管理內容。 應用程式需負責透過 <xref:System.ServiceModel.Channels.ContextMessageProperty> 來擷取、管理與套用內容。 任何嘗試呼叫 `GetContext` 或 `SetContext` 的行為都會導致 <xref:System.InvalidOperationException>。  
  
 不管選擇了哪一種模式，用戶端通道處理站都會支援 <xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IRequestSessionChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 訊息交換模式。  
  
 對服務來說，通道的執行個體負責將傳入訊息上由用戶端提供的內容，轉換為 <xref:System.ServiceModel.Channels.ContextMessageProperty>。 訊息屬性可以接著由應用程式層或是呼叫堆疊中更上層的其他通道來存取。 服務通道同時可允許應用程式層藉由將 <xref:System.ServiceModel.Channels.ContextMessageProperty> 附加至回應訊息，以指定要傳播回用戶端的新內容值。 視繫結的組態而定，這個屬性會轉換成包含內容的 SOAP 標頭或 HTTP Cookie。 服務通道接聽項支援 <xref:System.ServiceModel.Channels.IReplyChannel>、<xref:System.ServiceModel.Channels.IReplySessionChannel> 和 <xref:System.ServiceModel.Channels.IReplySessionChannel> 訊息交換模式。  
  
 內容交換通訊協定引進了新的 `wsc:Context` SOAP 標頭，可在未使用 HTTP Cookie 來傳播內容時，用來代表內容資訊。 內容標頭結構描述允許任何數量的子項目存在，其中每一個都包含一個字串索引鍵與字串內容。 下列是內容標頭的範例。  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 在 `HttpCookie` 模式中，Cookie 會透過 `SetCookie` 標頭來設定。 Cookie 的名稱是 `WscContext`。 Cookie 的值是 `wsc:Context` 標頭的 Base64 編碼。 此值會以引號包住。  
  
 傳輸中的內容值必須加以保護以免遭到修改，所持理由與保護 WS-Addressing 標頭一樣，因為標頭是用來決定要求將分派到服務的哪個位置。 因此當繫結提供訊息保護功能時，便需要針對 `wsc:Context` 標頭在 SOAP 或傳輸層級進行數位簽署或是簽署加上加密處理。 一旦使用 HTTP Cookie 來傳播內容，就應該透過傳輸安全性來保護這些 Cookie 的安全。  
  
 服務端點可以在發行的原則中明確地陳述對內容交換通訊協定的支援需求。 兩個全新的原則判斷提示已經引進來代表用戶端需求，以支援 SOAP 層級的內容交換通訊協定或是啟用 HTTP Cookie 支援。 服務原則中會不會產生這些判斷提示是由如下列所示的 <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> 屬性值所控制：  
  
-   對 <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader> 來說，會產生下列判斷提示：  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   對 <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie> 來說，會產生下列判斷提示：  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Web 服務通訊協定互通性手冊](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
