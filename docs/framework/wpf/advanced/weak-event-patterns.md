---
title: "弱式事件模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件處理常式, 弱式事件模式"
  - "IWeakEventListener 介面"
  - "弱式事件模式實作"
  - "WeakEventManager 類別"
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 弱式事件模式
在應用程式中，在與將處理常式附加到來源的接聽項物件搭配使用時，很可能不會終結附加到事件來源的處理常式。  這種情況可能會導致記憶體遺漏 \(Memory Leak\)。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 引入的設計模式可以用來解決這個問題，方法是藉由提供專屬的管理員類別給特定事件，並在該事件的接聽項上實作介面。  這個設計模式稱為「*弱式事件模式*」。  
  
## 為何要實作弱式事件模式  
 接聽事件可能會導致記憶體遺漏。  一般用於接聽事件的技術，是使用語言特定的語法來附加處理常式到來源事件。  例如，在 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 中，語法是 `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。  
  
 這個技術會建立事件來源對事件接聽項的強式參考。  一般而言，為接聽項附加事件處理常式會讓接聽項的物件存留期受到來源物件存留期的影響 \(除非明確移除事件處理常式\)。  但在有些情況下，您會希望接聽項的物件存留期只受到其他因素的控制，例如接聽項目前是否屬於應用程式的視覺化樹狀結構中，而不希望受到來源的存留期控制。  一旦來源物件存留期超過接聽項的物件存留期時，一般的事件模式會導致記憶體遺漏：接聽項存留的時間比預期長。  
  
 弱式事件模式就是設計來解決這個記憶體遺漏問題。  弱式事件模式可用於當接聽項需要註冊事件，但未確切了解應在何時取消註冊的時候。  當來源的物件存留期超過接聽項可用的物件存留期時，也能使用弱式事件模式   \(在這種情況下，此處的 *useful* 是由您決定的\)。 弱式事件模式可以在不以任何方式影響接聽項的物件存留期特性的情況下，允許接聽項註冊和接收事件。  實際上，在決定接聽項是否適合記憶體回收時，並不會判斷來源的隱含參考。  該參考是弱式參考，因而命名為弱式事件模式和相關的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  接聽項可以經記憶體回收或由其他方式終結，且來源可以繼續，而不需要保留不可回收的處理常式參考給現在已終結的物件。  
  
## 哪些人應該實作弱式事件模式  
 會對實作弱式事件模式有興趣的人主要是控制項作者。  身為控制項作者，您主要負責控制項的行為和內含項目，以及控制項對於其插入的應用程式的影響。  這包括控制項物件存留期行為，特別是有關所描述的記憶體遺漏問題的處理。  
  
 某些案例本身就提供弱式事件模式的應用。  資料繫結便屬於這類型的案例。  在資料繫結中，來源物件通常和接聽項物件 \(繫結的目標\) 完全無關。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資料繫結的許多方面中，弱式事件模式已套用在事件的實作方式上。  
  
## 如何實作弱式事件模式  
 有三種方法可以實作弱式事件模式。  下表列出三種方法，並且提供當您使用的一些指引。  
  
|處理方式|若要實作的時機|  
|----------|-------------|  
|使用現有的弱式事件管理員類別|如果您想要訂閱該的事件擁有對應<xref:System.Windows.WeakEventManager>，使用現有的弱式事件管理員。  隨附於 WPF 的弱式事件管理員 」 的清單，請參閱繼承階層架構，在<xref:System.Windows.WeakEventManager>類別。  不過，要注意的是，有很少會隨附 WPF 中，所以您可能要選擇其他解決方法的其中一種的弱式事件管理員。|  
|使用一般的弱式事件管理員類別|使用泛型<xref:System.Windows.WeakEventManager%602>現有<xref:System.Windows.WeakEventManager>無法使用，您希望可以輕鬆地實作，而您不擔心效率。  一般<xref:System.Windows.WeakEventManager%602>的效能略高於現有或自訂的弱式事件管理員。  例如，泛型類別會詳細反映來探索事件指定事件名稱。  此外，程式碼來使用一般來註冊事件<xref:System.Windows.WeakEventManager%602>會較比起使用現有或自訂<xref:System.Windows.WeakEventManager>。|  
|建立自訂的弱式事件管理員類別|建立自訂的<xref:System.Windows.WeakEventManager>時您現有的<xref:System.Windows.WeakEventManager>就無法使用，而您想最佳的效率。  使用自訂的<xref:System.Windows.WeakEventManager>來訂閱事件將會更有效率，但您不要對撰寫更多的程式碼開始的成本。|  
  
 下列章節說明如何實作弱式事件模式。  為了這個討論區的詳細資訊，以訂閱該事件具有下列特性。  
  
-   事件的名稱是`SomeEvent`。  
  
-   藉由引發事件`EventSource`類別。  
  
-   事件處理常式具有型別： `SomeEventEventHandler` \(或`EventHandler<SomeEventEventArgs>`\)。  
  
-   這個事件會傳遞一個型別的參數`SomeEventEventArgs`事件處理常式。  
  
### 使用現有的弱式事件管理員類別  
  
1.  尋找現有的弱式事件管理員。  
  
     隨附於 WPF 的弱式事件管理員 」 的清單，請參閱繼承階層架構，在<xref:System.Windows.WeakEventManager>類別。  
  
2.  使用新的弱式事件管理員，而非一般事件連結。  
  
     例如，如果您的程式碼會使用下列模式來訂閱事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果程式碼的事件取消訂閱使用下列模式：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### 使用泛型的弱式事件管理員類別  
  
1.  使用泛用<xref:System.Windows.WeakEventManager%602>類別，而非一般事件連結。  
  
     當您使用<xref:System.Windows.WeakEventManager%602>註冊事件接聽程式，您提供事件來源和<xref:System.EventArgs>的類別和呼叫的型別參數的型別<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下列程式碼所示：  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### 建立自訂的弱式事件管理員類別  
  
1.  將下列類別範本複製到您的專案。  
  
     這個類別是繼承自 <xref:System.Windows.WeakEventManager> 類別。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  取代`SomeEventWeakEventManager`名稱與您的名字。  
  
3.  取代為您的事件對應的名稱與先前所述的三個名稱。  \(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`\)  
  
4.  弱式事件管理員類別的可視性 \(公用 \/ 內部 \/ 私用\) 設為它管理的事件相同的可視性。  
  
5.  使用新的弱式事件管理員，而非一般事件連結。  
  
     例如，如果您的程式碼會使用下列模式來訂閱事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果程式碼的事件取消訂閱使用下列模式：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## 請參閱  
 <xref:System.Windows.WeakEventManager>   
 <xref:System.Windows.IWeakEventListener>   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)