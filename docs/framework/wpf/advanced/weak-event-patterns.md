---
title: 弱式事件模式
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: e0cd6837de626fa6bcd560811c6a70f7f6604daa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316163"
---
# <a name="weak-event-patterns"></a>弱式事件模式
在應用程式，它可能會附加到事件來源的處理常式不會終結協調的方式處理常式附加至來源接聽程式物件。 這種情況可能會導致記憶體流失無關。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 導入了可用來解決這個問題，提供的專用的管理員類別的特定事件，並針對該事件的接聽程式上實作介面的設計模式。 這種設計模式就所謂*弱式事件模式*。  
  
## <a name="why-implement-the-weak-event-pattern"></a>為何要實作弱式事件模式？  
 接聽事件可能會導致記憶體流失。 接聽事件的一般技巧是使用將處理常式附加至事件來源上的特定語言的語法。 例如，在C#，語法是： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。  
  
 這項技術會建立強式參考從事件來源的事件接聽程式。 一般情況下，將事件處理常式附加接聽程式會造成接聽程式 （除非明確移除事件處理常式），會受到來源的物件存留期物件存留期。 但在某些情況下，您可能想要其他因素所控制的接聽程式的物件存留期例如是否目前屬於視覺化樹狀結構的應用程式，而不是由來源的存留期。 一般事件模式時的來源物件存留期超出接聽程式的物件存留期時，會導致記憶體流失： 接聽程式存留的時間比預期長。  
  
 弱式事件模式是設計用來解決此記憶體流失問題。 接聽程式需要註冊事件，但是接聽程式不會明確知道何時要取消註冊時，可以使用弱式事件模式。 每當來源的物件存留期超過有用的物件存留期，接聽程式時，可以也使用弱式事件模式。 (在此情況下，*有用*由您決定。)弱式事件模式可讓註冊和接收事件，而不會影響物件存留期特性，以任何方式接聽程式接聽程式。 作用中，從來源的隱含的參考不會判斷是否適合進行記憶體回收的接聽程式。 參考是弱式參考，因此命名的弱式事件模式和相關[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 接聽程式可以是記憶體回收或否則損毀，而且來源可以繼續，而不需要保留構成處理常式現在已終結的物件參考。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>誰應該實作弱式事件模式？  
 實作弱式事件模式有趣的是主要是針對控制項作者。 身為控制項作者，您負責大部分的行為與您的控制項和它對應用程式，它會插入影響的內含項目。 這包括控制物件存留期行為，特別是處理的所述的記憶體流失的問題。  
  
 某些情況下原本就是讓他們的弱式事件模式的應用程式。 這類案例之一是資料繫結。 在資料繫結，它是很常見的來源物件是完全獨立於接聽程式物件，因為它是繫結的目標項目。 許多層面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料繫結已經具有弱式事件模式中事件的實作方式套用。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>如何實作弱式事件模式  
 有三種方式可以實作弱式事件模式。 下表列出這三種方法，並提供一些指引，當您應該使用的每個。  
  
|方法|何時實作|  
|--------------|-----------------------|  
|使用現有的弱式事件管理員類別|如果您想要訂閱的事件都有對應<xref:System.Windows.WeakEventManager>，使用現有的弱式事件管理員。 WPF 隨附的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。 包含的弱式事件管理員是有限的因為您可能必須選擇其中一種其他方法。|  
|使用一般的弱式事件管理員類別|使用泛型<xref:System.Windows.WeakEventManager%602>時的現有<xref:System.Windows.WeakEventManager>無法使用，您想要輕鬆地實作，且您不擔心效率。 泛型<xref:System.Windows.WeakEventManager%602>效率比現有或自訂的弱式事件管理員。 比方說，泛型類別會執行更多的反映，來探索指定的事件名稱的事件。 此外，程式碼以註冊事件，藉由使用泛型<xref:System.Windows.WeakEventManager%602>更詳細資訊，比使用現有或自訂<xref:System.Windows.WeakEventManager>。|  
|建立自訂的弱式事件管理員類別|建立自訂<xref:System.Windows.WeakEventManager>時的現有<xref:System.Windows.WeakEventManager>不提供，而且您想最佳的效率。 使用自訂<xref:System.Windows.WeakEventManager>訂閱事件將會更有效率，但是否會負擔撰寫更多的程式碼開頭的成本。|  
|使用第三方弱式事件管理員|NuGet 已[幾個弱式事件管理員](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)許多 WPF 架構還支援模式 (比方說，請參閱[Prism 的鬆散偶合的事件訂用帳戶上的文件](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events))。|

 下列各節說明如何實作弱式事件模式。  基於本文的討論，要訂閱事件具有下列特性。  
  
-   事件名稱是`SomeEvent`。  
  
-   引發事件`EventSource`類別。  
  
-   事件處理常式都已型別： `SomeEventEventHandler` (或`EventHandler<SomeEventEventArgs>`)。  
  
-   這個事件會傳遞為參數的型別`SomeEventEventArgs`的事件處理常式。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>使用現有的弱式事件管理員類別  
  
1. 尋找現有的弱式事件管理員。  
  
     WPF 隨附的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。  
  
2. 使用新的弱式事件管理員，而不是一般事件連結。  
  
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
  
1. 使用泛型<xref:System.Windows.WeakEventManager%602>類別而不是一般事件連結。  
  
     當您使用<xref:System.Windows.WeakEventManager%602>若要註冊事件接聽程式，您會提供事件來源與<xref:System.EventArgs>型別做為型別參數至類別，並呼叫<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下列程式碼所示：  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>建立自訂的弱式事件管理員類別  
  
1. 將下列類別範本複製到您的專案中。  
  
     這個類別繼承自<xref:System.Windows.WeakEventManager>類別。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. 取代`SomeEventWeakEventManager`名稱與您自己的名稱。  
  
3. 取代為您的活動相對應的名稱與先前所述的三個名稱。 (`SomeEvent`， `EventSource`，和`SomeEventEventArgs`)  
  
4. 若要為其所管理的事件相同的可視性設定弱式事件管理員類別的可視性 （公用 / 內部 / 私用）。  
  
5. 使用新的弱式事件管理員，而不是一般事件連結。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [路由事件概觀](routed-events-overview.md)
- [資料繫結概觀](../data/data-binding-overview.md)
