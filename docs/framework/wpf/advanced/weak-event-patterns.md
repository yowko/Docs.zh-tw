---
title: 弱式事件模式
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991793"
---
# <a name="weak-event-patterns"></a>弱式事件模式
在應用程式中，附加到事件來源的處理常式可能不會在與附加處理常式至來源的接聽程式物件協調時遭到破壞。 這種情況可能會導致記憶體流失。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]引進一種設計模式，可以用來解決這個問題，方法是提供特定事件的專用管理員類別，並在該事件的接聽程式上執行介面。 這個設計模式就是所謂的「*弱式事件模式*」。  
  
## <a name="why-implement-the-weak-event-pattern"></a>為什麼要執行弱式事件模式？  
 接聽事件可能會導致記憶體流失。 接聽事件的一般方法是使用特定語言的語法，將處理常式附加至來源上的事件。 例如，在中C#，該語法為： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。  
  
 這項技術會建立從事件來源到事件接聽程式的強式參考。 通常，附加接聽項的事件處理常式會導致接聽程式具有受來源物件存留期影響的物件存留期（除非明確地移除事件處理常式）。 但在某些情況下，您可能想要讓接聽程式的物件存留期受到其他因素的控制，例如它目前是否屬於應用程式的視覺化樹狀結構，而不是來源的存留期。 每當來源物件存留期延伸超出接聽程式的物件存留期時，一般事件模式就會導致記憶體流失：接聽程式的存留時間比預期的長。  
  
 弱式事件模式的設計目的是要解決這個記憶體流失的問題。 每當接聽程式需要註冊事件時，就可以使用弱式事件模式，但是接聽程式並不明確知道何時取消註冊。 只要來源的物件存留期超過接聽程式的有用物件存留期，也可以使用弱式事件模式。 （在此案例中，*有用*的是由您所決定）。弱式事件模式可讓接聽程式註冊並接收事件，而不會以任何方式影響接聽項的物件存留期特性。 實際上，來自來源的隱含參考不會判斷接聽程式是否符合垃圾收集的資格。 參考是弱式參考，因此會命名弱式事件模式和相關的 Api。 接聽程式可以進行垃圾收集或以其他方式終結，而來源可以繼續，而不會保留目前已損毀物件的構成處理常式參考。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>誰應該實行弱式事件模式？  
 執行弱式事件模式主要是對控制項作者感興趣。 身為控制項作者，您主要負責控制控制項的行為和內含專案，以及它對插入它的應用程式所造成的影響。 這包括控制物件存留期行為，特別是處理所述記憶體流失的問題。  
  
 某些案例原本就是將自己帶到弱式事件模式的應用程式。 其中一種情況就是資料系結。 在 [資料系結] 中，來源物件與接聽程式物件完全獨立，這是系結的目標。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料系結的許多層面已經有在事件的執行方式中所套用的弱式事件模式。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>如何執行弱式事件模式  
 有三種方式可執行弱式事件模式。 下表列出這三種方法，並提供一些使用時機的指引。  
  
|方法|執行時機|  
|--------------|-----------------------|  
|使用現有的弱式事件管理員類別|如果您要訂閱的事件具有對應<xref:System.Windows.WeakEventManager>的，請使用現有的弱式事件管理員。 如需 WPF 隨附之弱式事件管理員的清單，請參閱<xref:System.Windows.WeakEventManager>類別中的繼承階層架構。 由於內含的弱式事件管理員受到限制，因此您可能需要選擇其中一種方法。|  
|使用一般弱式事件管理員類別|<xref:System.Windows.WeakEventManager%602>當現有<xref:System.Windows.WeakEventManager>的無法使用時，您需要簡單的方法來執行，而且您不在意效率。 一般<xref:System.Windows.WeakEventManager%602>比現有或自訂弱式事件管理員更有效率。 例如，泛型類別會執行更多反映，以便在指定事件名稱的情況下探索事件。 此外，使用泛型<xref:System.Windows.WeakEventManager%602>來註冊事件的程式碼，比使用現有或自訂<xref:System.Windows.WeakEventManager>更詳細。|  
|建立自訂弱式事件管理員類別|當現有<xref:System.Windows.WeakEventManager> <xref:System.Windows.WeakEventManager>的無法使用，且您想要獲得最佳效率時，請建立自訂。 使用自訂<xref:System.Windows.WeakEventManager>的來訂閱事件將會更有效率，但在一開始就會產生更多程式碼的成本。|  
|使用協力廠商弱式事件管理員|NuGet 有[數個弱式事件管理員](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)，而許多 WPF 架構也支援模式（例如，請參閱[Prism 的檔，以取得鬆散結合的事件訂](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)用帳戶）。|

 下列各節說明如何執行弱式事件模式。  基於此討論的目的，訂閱的事件具有下列特性。  
  
- 事件名稱為`SomeEvent`。  
  
- 事件是由`EventSource`類別引發。  
  
- 事件處理常式的類型為`SomeEventEventHandler` ：（ `EventHandler<SomeEventEventArgs>`或）。  
  
- 事件會將類型`SomeEventEventArgs`的參數傳遞給事件處理常式。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>使用現有的弱式事件管理員類別  
  
1. 尋找現有的弱式事件管理員。  
  
     如需 WPF 隨附之弱式事件管理員的清單，請參閱<xref:System.Windows.WeakEventManager>類別中的繼承階層架構。  
  
2. 使用新的弱式事件管理員，而不是一般事件連結。  
  
     例如，如果您的程式碼使用下列模式來訂閱事件：  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     將它變更為下列模式：  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果您的程式碼使用下列模式來取消訂閱事件：  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     將它變更為下列模式：  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>使用一般弱式事件管理員類別  
  
1. 使用泛型<xref:System.Windows.WeakEventManager%602>類別，而不是一般事件連結。  
  
     當您使用<xref:System.Windows.WeakEventManager%602>註冊事件接聽程式時，您會提供事件來源<xref:System.EventArgs>和類型做為類別的型別參數， <xref:System.Windows.WeakEventManager%602.AddHandler%2A>並呼叫，如下列程式碼所示：  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>建立自訂弱式事件管理員類別  
  
1. 將下列類別範本複製到您的專案。  
  
     這個類別繼承自<xref:System.Windows.WeakEventManager>類別。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. 將名稱`SomeEventWeakEventManager`取代為您自己的名稱。  
  
3. 將先前所述的三個名稱取代為您事件的對應名稱。 （`SomeEvent`、 `EventSource`和）`SomeEventEventArgs`  
  
4. 將弱式事件管理員類別的可見度（公用/內部/私用）設定為與它所管理之事件相同的可見度。  
  
5. 使用新的弱式事件管理員，而不是一般事件連結。  
  
     例如，如果您的程式碼使用下列模式來訂閱事件：  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     將它變更為下列模式：  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同樣地，如果您的程式碼使用下列模式來取消訂閱事件：  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     將它變更為下列模式：  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [路由事件概觀](routed-events-overview.md)
- [資料繫結概觀](../data/data-binding-overview.md)
