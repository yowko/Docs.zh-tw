---
title: "弱式事件模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21a36797f945f37a641e7002bbb9937a664650fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="weak-event-patterns"></a>弱式事件模式
在應用程式，它可能會附加到事件來源的處理常式不會終結搭配此處理常式附加到來源的接聽程式物件。 這種情況可能會導致記憶體流失無關。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]導入了可用來解決這個問題，提供專用的管理員類別的特定事件，該事件的接聽項上實作介面的設計模式。 此設計模式又稱為*弱式事件模式*。  
  
## <a name="why-implement-the-weak-event-pattern"></a>為什麼實作弱式事件模式？  
 接聽事件可能會導致記憶體流失。 接聽事件的典型技巧是使用附加至來源上的事件處理常式的特定語言的語法。 例如，在[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]，語法是： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。  
  
 這項技術建立的事件接聽程式從事件來源的強式參考。 一般來說，附加事件處理常式，接聽程式會導致物件存留期 （除非明確移除事件處理常式），會受到來源的物件存留期，接聽程式。 但在某些情況下，您可能想物件存留期的接聽程式會由其他因素，例如是否目前屬於應用程式，而不是由來源的存留期的視覺化樹狀結構。 一般事件模式時的來源物件存留期超出接聽程式的物件存留期時，會導致記憶體流失： 接聽程式就會保持運作時間比預期長。  
  
 弱式事件模式是設計用來解決此記憶體流失問題。 每當需要註冊事件接聽程式，但是接聽程式無法明確知道何時要取消註冊時，可以使用弱式事件模式。 來源的物件存留期超過有用的物件存留期的接聽程式時，也可以使用弱式事件模式。 (在此情況下，*有用*由您決定。)弱式事件模式可讓要註冊，且不會影響物件存留期的特性以任何方式接聽程式接收到事件的接聽程式。 作用中，從來源的隱含的參考不會判斷是否接聽程式都可進行記憶體回收。 參考是弱式參考，因此命名的弱式事件模式和相關[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 接聽程式可以是記憶體回收或其他方式終結，和來源可以繼續，但不保留不可回收處理常式現在已終結物件參考。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>人員應該實作弱式事件模式？  
 實作弱式事件模式有趣的是主要用於控制項作者。 控制項的作者，會負責的行為與您的控制項及插入它的應用程式之影響的內含項目。 這包括控制項物件存留期行為，特別是描述的記憶體流失問題的處理。  
  
 某些情況下原本就是應用程式為自己弱式事件模式的應用程式。 這類案例之一是資料繫結。 在資料繫結，是很常見的來源物件變成完全獨立的接聽程式物件，因為它是繫結的目標。 許多層面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料繫結已經具有弱式事件模式中事件的實作方式套用。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>如何實作弱式事件模式  
 有三種方式來實作弱式事件模式。 下表列出這三種方法，並提供一些您應該何時使用每個的指引。  
  
|方法|何時實作|  
|--------------|-----------------------|  
|使用現有的弱式事件管理員類別|如果您想要訂閱的事件都有對應<xref:System.Windows.WeakEventManager>，使用現有的弱式事件管理員。 如需包含 WPF 的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。 不過，請注意，有相對較少的弱式事件管理員隨附的 WPF 中，因此您可能需要選擇其中一種其他方法。|  
|使用一般的弱式事件管理員類別|使用泛型<xref:System.Windows.WeakEventManager%602>時的現有<xref:System.Windows.WeakEventManager>無法使用，您想要輕鬆地實作，而且您不擔心效率。 泛型<xref:System.Windows.WeakEventManager%602>比現有或自訂的弱式事件管理員比較沒有效率。 例如，泛型類別會詳細反映來探索事件指定事件的名稱。 此外，程式碼以使用泛型來註冊事件<xref:System.Windows.WeakEventManager%602>更詳細資訊，比使用的現有或自訂<xref:System.Windows.WeakEventManager>。|  
|建立自訂的弱式事件管理員類別|建立自訂<xref:System.Windows.WeakEventManager>時的現有<xref:System.Windows.WeakEventManager>不提供，而且您想最佳的效率。 使用自訂<xref:System.Windows.WeakEventManager>來訂閱事件將會更有效率，但您沒有承受撰寫更多的程式碼開頭的成本。|  
  
 下列章節說明如何實作弱式事件模式。  基於本討論內容的詳細資訊，來訂閱事件具有下列特性。  
  
-   事件名稱`SomeEvent`。  
  
-   引發事件`EventSource`類別。  
  
-   此事件處理常式有型別： `SomeEventEventHandler` (或`EventHandler<SomeEventEventArgs>`)。  
  
-   這個事件會傳遞的型別參數`SomeEventEventArgs`的事件處理常式。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>使用現有的弱式事件管理員類別  
  
1.  管理員尋找現有的弱式事件。  
  
     如需包含 WPF 的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。  
  
2.  使用新的弱式事件管理員，而不是一般事件連結。  
  
     例如，如果您的程式碼使用下列模式來訂閱事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果您的程式碼使用下列模式來取消訂閱事件：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>使用泛型的弱式事件管理員類別  
  
1.  使用泛型<xref:System.Windows.WeakEventManager%602>類別而不是一般事件連結。  
  
     當您使用<xref:System.Windows.WeakEventManager%602>註冊事件接聽程式，您會提供事件來源和<xref:System.EventArgs>做為類別，然後呼叫型別參數的型別<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下列程式碼所示：  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>建立自訂的弱式事件管理員類別  
  
1.  將下列類別範本複製到您的專案。  
  
     此類別繼承自<xref:System.Windows.WeakEventManager>類別。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  取代`SomeEventWeakEventManager`名稱與您自己的名稱。  
  
3.  取代對應事件的名稱與先前所述的三個名稱。 (`SomeEvent`， `EventSource`，和`SomeEventEventArgs`)  
  
4.  設為其所管理的事件相同的可見性的可見性 （公用 / 內部 / 私用） 弱式事件管理員類別。  
  
5.  使用新的弱式事件管理員，而不是一般事件連結。  
  
     例如，如果您的程式碼使用下列模式來訂閱事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果您的程式碼使用下列模式來取消訂閱事件：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     請將它變更為下列模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)
