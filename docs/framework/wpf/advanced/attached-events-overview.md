---
title: 附加事件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141558"
---
# <a name="attached-events-overview"></a>附加事件概觀

可延伸應用程式標記語言 （XAML） 定義稱為*附加事件*的語言元件和事件種類。 附加事件的概念，讓您能新增特定事件的處理常式到任意項目，而不是實際定義或繼承事件的項目。 在此情況下，可能引發事件的物件和目的地處理執行個體都不會定義或以其他方式「擁有」事件。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[路由事件概觀](routed-events-overview.md)和 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>附加事件語法  
 附加的事件具有 XAML 語法和編碼模式，備份代碼必須使用該模式才能支援附加的事件使用。  
  
 在 XAML 語法中，附加的事件不僅由其事件名稱指定，還由其所屬類型加上事件名稱指定，由點 （.） 分隔。 因為事件名稱以其擁有類型的名稱來限定，附加事件語法可讓任何附加事件附加至可以具現化的任何項目。  
  
 例如，以下是用於附加自訂`NeedsCleaning`附加事件的處理常式的 XAML 語法：  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 請注意 `aqua:` 前置詞，前置詞在此情況中是必要的，因為附加事件是來自自訂對應 xmlns 的自訂事件。  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>WPF 如何實作附加事件

在 WPF 中，附加的事件由<xref:System.Windows.RoutedEvent>欄位備份，並在引發後通過樹路由它們。 一般而言，附加事件的來源 (引發事件的物件) 是系統或服務來源，因此執行引發事件之程式碼的物件不直接是項目樹狀結構的一部分。  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>附加事件的情節  
 在 WPF 中，附加事件存在於存在服務等級抽象的某些功能區域，例如對於靜態<xref:System.Windows.Input.Mouse>類或<xref:System.Windows.Controls.Validation>類啟用的事件。 與服務互動或是使用服務的類別可以以附加事件語法使用事件，或者它們可以選擇將附加事件公開為路由事件，路由事件是類別整合服務功能的方式之一。  
  
 儘管 WPF 定義了許多附加事件，但直接使用或處理附加事件的情況非常有限。 通常，附加事件具有體系結構目的，但隨後將轉發到未附加（帶有 CLR 事件"包裝器"的路由事件）。  
  
 <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>例如，通過在給定的<xref:System.Windows.UIElement>上面使用<xref:System.Windows.UIElement.MouseDown>，而不是在 XAML 或代碼中處理附加<xref:System.Windows.UIElement>的事件語法，可以更輕鬆地處理基礎附加事件。 附加事件在架構中有其用途，因為它可讓您在未來擴充輸入裝置。 假設設備只需要提高<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>，以類比滑鼠輸入，並且不需要派生<xref:System.Windows.Input.Mouse>來執行此操作。 但是，此方案涉及事件的代碼處理，並且附加事件的 XAML 處理與此方案無關。  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>在 WPF 中處理附加事件  
 處理附加事件的程序，以及您將撰寫的處理常式程式碼，基本上與路由事件一樣。  
  
 通常，WPF 附加事件與 WPF 路由事件沒有很大區別。 差異是事件的來源方式以及類作為成員如何公開事件（這也會影響 XAML 處理常式語法）。  
  
 但是，如前所述，現有的 WPF 附加事件並非特別適用于在 WPF 中處理。 更常見的是，事件的目的是要在複合 (compositing) 中啟用報告狀態給父項目的複合項目，在此情況下，事件通常會在程式碼中引發，並依賴相關父類別中的類別處理。 例如，應引發<xref:System.Windows.Controls.Primitives.Selector>附加<xref:System.Windows.Controls.Primitives.Selector.Selected>事件，然後<xref:System.Windows.Controls.Primitives.Selector>由類處理該事件，然後由<xref:System.Windows.Controls.Primitives.Selector>類可能將其轉換為其他路由事件 。 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 如需路由事件與類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>將您自己的附加事件定義為路由事件  
 如果要從常見的 WPF 基類派生，則可以通過在類中包括某些模式方法並使用基類上已經存在的實用程式方法來實現您自己的附加事件。  
  
 模式如下所示︰  
  
- 方法添加具有兩個參數__*的事件名稱*處理常式__。 第一個參數是向其添加事件處理常式的實例。 第二個參數是要添加的事件處理常式。 方法必須為`public`和`static`，沒有傳回值。  
  
- 方法刪除具有兩個參數__*的事件名稱*處理常式__。 第一個參數是從中刪除事件處理常式的實例。 第二個參數是要刪除的事件處理常式。 方法必須為`public`和`static`，沒有傳回值。  
  
 在元素上聲明附加的事件處理常式屬性時，__添加*事件名稱*處理常式__訪問器方法有助於 XAML 處理。 __添加*事件名稱*處理常式__和__刪除*事件名稱*處理常式__方法還允許對附加事件的事件處理常式存儲進行代碼訪問。  
  
 此常規模式還不足以在框架中實際實現，因為任何給定的 XAML 讀取器實現可能具有不同的方案來標識支援語言和體系結構中的基礎事件。 這是 WPF 將附加事件作為路由事件實現的原因之一;用於事件 （<xref:System.Windows.RoutedEvent>） 的識別碼已由 WPF 事件系統定義。 此外，路由事件是附加事件的 XAML 語言級別概念的自然實現擴展。  
  
 WPF 附加事件的__添加*事件名稱*處理常式__實現包括將<xref:System.Windows.UIElement.AddHandler%2A>路由事件和處理常式調用作為參數。  
  
 此實現策略和路由事件系統通常將附加事件的處理限制為<xref:System.Windows.UIElement>派生類或<xref:System.Windows.ContentElement>派生類，因為只有這些類具有<xref:System.Windows.UIElement.AddHandler%2A>實現。  
  
 例如，以下代碼定義擁有者類`NeedsCleaning``Aquarium`上的附加事件，使用 WPF 附加的事件策略將附加事件聲明為路由事件。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 請注意，用於建立附加事件識別碼欄位<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>的方法 實際上是用於註冊非附加路由事件的方法。 附加事件和路由事件全都註冊到集中式內部存放區。 此事件存放區實作促成了[路由事件概觀](routed-events-overview.md)中所討論的「事件即介面」概念考量。  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>引發 WPF 附加事件  
 您通常不需要從代碼中引發現有的 WPF 定義的附加事件。 這些事件遵循一般"服務"概念模型，服務類（如<xref:System.Windows.Input.InputManager>負責引發事件）。  
  
 但是，如果您正在基於基於 附加事件的 WPF 模型定義<xref:System.Windows.RoutedEvent>自訂附加事件，則可以使用<xref:System.Windows.UIElement.RaiseEvent%2A>從 任何<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>引發附加事件。 引發路由事件（附加或不附加）要求您將元素樹中的特定元素聲明為事件源;否則，將元素聲明為事件源。該源報告為<xref:System.Windows.UIElement.RaiseEvent%2A>調用方。 判斷樹狀結構中的哪個項目報告為來源是服務的責任  
  
## <a name="see-also"></a>另請參閱

- [路由事件概觀](routed-events-overview.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
