---
title: "自訂資料流升級 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 自訂資料流升級
以資料流為導向的傳輸 \(例如 TCP 和具名管道\) 會在用戶端和伺服器之間的連續位元組資料流上進行作業。  透過 <xref:System.IO.Stream> 物件即可實現此資料流。  在資料流升級中，用戶端會想將選用通訊協定層新增至通道堆疊，並也要求其他通訊通道端也這樣執行。  資料流升級包含使用升級的物件取代原始的 <xref:System.IO.Stream> 物件。  
  
 例如，您可以直接在傳輸資料流的上方建立壓縮資料流。  在這個情況下，會使用包裝壓縮 <xref:System.IO.Stream> \(繞著原始的物件\) 的物件取代原始傳輸 <xref:System.IO.Stream>。  
  
 您可套用多個資料流升級，每一個都包裝前一個。  
  
## 資料流升級的運作方式  
 資料流升級處理序包含了四個元件。  
  
1.  升級資料流「*啟動器*」\(Initiator\) 會開始處理序：在執行階段會初始化其連線之另一端的要求，以升級通道傳輸層。  
  
2.  升級資料流「*接受器*」\(Acceptor\) 會執行升級：在執行階段會接收來自其他電腦的升級要求，可能的話會接受升級。  
  
3.  升級「*提供者*」\(Provider\) 會在用戶端上建立「*啟動器*」\(Initiator\)，並在伺服器上建立「*接受器*」\(Acceptor\)。  
  
4.  資料流升級「*繫結項目*」\(Binding Element\) 會新增至服務和用戶端上的繫結，並在執行階段建立提供者。  
  
 在多重升級的狀況中請特別注意，啟動器和接受器會封裝狀態機器，以強制執行可用於每次初始化的升級轉換。  
  
## 如何實作資料流升級  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供四個可讓您實作的 `abstract` 類別：  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=fullName>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=fullName>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=fullName>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=fullName>  
  
 若要實作自訂資料流升級，請執行下列動作。  這個程序會同時在用戶端和伺服器電腦上實作最小的資料流升級處理序。  
  
1.  建立會實作 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator> 的類別。  
  
    1.  覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> 方法以讓資料流進行升級，並傳回升級的資料流。  這個方法會以同步方式執行，也會有使用非同步方式初始化升級的類似方法。  
  
    2.  覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> 方法以檢查其他升級。  
  
2.  建立會實作 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor> 的類別。  
  
    1.  覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> 方法以讓資料流進行升級，並傳回升級的資料流。  這個方法會以同步方式執行，也會有使用非同步方式接受升級的類似方法。  
  
    2.  覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> 方法以判斷此時升級處理序中的升級接受器是否支援所要求的升級。  
  
3.  建立會實作 <xref:System.ServiceModel.Channels.StreamUpgradeProvider> 的類別。  覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> 和 <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> 方法，以傳回在步驟 2 和 1 中所定義的接受器和啟動器執行個體。  
  
4.  建立會實作 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> 的類別。  
  
    1.  覆寫用戶端上的 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> 方法和服務上的 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> 方法。  
  
    2.  覆寫用戶端上的 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 方法和服務上的 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 方法，以將升級繫結項目新增至 <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>。  
  
5.  將新資料流升級繫結項目新增至伺服器和用戶端電腦上的繫結。  
  
## 安全性升級  
 新增安全性升級是一般資料流升級處理序的特殊版本。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 已提供兩個繫結項目以用於升級資料流安全性。  傳輸層安全性的組態是由 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> 和 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> 所封裝，而您可以設定這兩項並新增至自訂繫結。  這些繫結項目會擴充 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> 類別，而這個類別會建置用戶端和伺服器的資料流升級提供者。  這些繫結項目擁有的方法會建立特殊的安全性資料流升級提供者類別 \(這些類別不是 `public`\)，因此對於這兩個類別來說，您只需要將繫結項目新增至繫結即可。  
  
 針對上述兩個繫結項目不符合的安全性案例，這三個與安全性相關的 `abstract` 類別都是衍生自上述的啟動器、接受器和提供者基底類別：  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=fullName>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=fullName>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=fullName>  
  
 實作安全性資料流升級的處理序和先前所述一樣，差別在於您需要從這三個類別中衍生其他項目。  覆寫這些類別中的其他屬性，以對執行階段提供安全性資訊。  
  
## 多重升級  
 若要建立其他升級要求，請重複上述處理序：建立 <xref:System.ServiceModel.Channels.StreamUpgradeProvider> 和繫結項目的其他延伸項目。  將繫結項目新增至繫結。  從第一個新增至繫結的繫結項目開始，循序處理其他繫結項目。  在 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 和 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 中，每個升級提供者都可以判斷如何在之前存在的升級繫結參數上自行分層。  接著應該以新的複合升級繫結參數來取代現有的升級繫結參數。  
  
 此外，一個升級提供者可以支援多個升級。  例如，您可能想要實作可同時支援安全性和壓縮的自訂資料流升級提供者。  請執行下列步驟：  
  
1.  子類別化 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> 以撰寫會建立啟動器和接受器的提供者類別。  
  
2.  子類別化 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> 以確定覆寫 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> 方法，進而按照順序傳回壓縮資料流和安全資料流的內容類型。  
  
3.  子類別化瞭解其 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> 方法之自訂內容類型的 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>。  
  
4.  每次呼叫 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> 和 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> 之後，就會升級資料流。  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>   
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>   
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>   
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>   
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>   
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>   
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>   
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>