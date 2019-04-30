---
title: 自訂動畫概觀
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: 268d218097233aee795154226cc6f7c3ce318f5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010146"
---
# <a name="custom-animations-overview"></a>自訂動畫概觀
本主題說明如何以及何時建立自訂主要畫面格、動畫類別來擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統，或使用每一畫面的回呼來略過它。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的不同動畫類型。 如需詳細資訊，請參閱＜From/To/By 動畫概觀＞、[主要畫面格動畫概觀](key-frame-animations-overview.md)以及[路徑動畫概觀](path-animations-overview.md)。  
  
 因為動畫類別繼承自<xref:System.Windows.Freezable>類別，您應該熟悉<xref:System.Windows.Freezable>物件，以及如何繼承自<xref:System.Windows.Freezable>。 如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>擴充動畫系統  
 有數種方式可以擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統，根據您想要使用的內建功能層級而定。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎中有三個主要擴充點︰  
  
- 建立自訂主要畫面格物件，藉由繼承自其中一個*\<類型 >* 主要畫面格類別，例如<xref:System.Windows.Media.Animation.DoubleKeyFrame>。 這個方法可使用大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎內建功能。  
  
- 建立您自己的動畫類別繼承自<xref:System.Windows.Media.Animation.AnimationTimeline>或其中一個*\<型別 >* AnimationBase 類別。  
  
- 您可以針對每一畫面格使用每一畫面的回呼來產生動畫。 這個方法完全略過動畫與計時系統。  
  
 下表說明一些擴充動畫系統的案例。  
  
|當您要...|使用這個方法|  
|-------------------------|-----------------------|  
|在有對應 *\<Type>* AnimationUsingKeyFrames 的類型值之間自訂內插補點|建立自訂主要畫面格。 如需詳細資訊，請參閱[建立自訂主要畫面格](#createacustomkeyframe)一節。|  
|不只是在有對應 *\<Type>* Animation 的類型值之間自訂內插補點。|建立自訂動畫類別，其繼承自和您想要以動畫顯示的類型對應的 *\<Type>* AnimationBase 類別。 如需詳細資訊，請參閱[建立自訂動畫類別](#createacustomanimationtype)一節。|  
|以動畫顯示沒有對應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類型的動畫|使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>或建立繼承自的類別<xref:System.Windows.Media.Animation.AnimationTimeline>。 如需詳細資訊，請參閱[建立自訂動畫類別](#createacustomanimationtype)一節。|  
|利用每個畫面格都會計算的值，並根據最後一組物件互動的值，以動畫顯示多個物件|使用每一畫面的回呼。 如需詳細資訊，請參閱[使用每一畫面的回呼](#useperframecallback)一節。|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>建立自訂主要畫面格  
 建立自訂主要畫面格類別是擴充動畫系統最簡單的方式。 當您想要不同的主要畫面格動畫內插補點方法時，請使用這個方法。  如[主要畫面格動畫概觀](key-frame-animations-overview.md)中所述，主要畫面格動畫使用主要畫面格物件來產生其輸出值。 每個主要畫面格物件都會執行三個函式︰  
  
- 指定目標值，使用其<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>屬性。  
  
- 指定的值應該到達的時間使用其<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性。  
  
- 藉由實作 InterpolateValueCore 方法，在前一個主要畫面格與其自身的值之間插入。  
  
 **實作指示**  
  
 衍生自 *\<Type>* KeyFrame 抽象類別並實作 InterpolateValueCore 方法。 InterpolateValueCore 方法會傳回主要畫面格目前的值。 它接受兩個參數︰前一個主要畫面格的值和範圍從 0 到 1 的進度值。 進度為 0 表示主要畫面格正好開始，值為 1 表示主要畫面格正好結束，並應該會傳回所指定的值及其<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>屬性。  
  
 因為*\<類型 >* KeyFrame 類別繼承自<xref:System.Windows.Freezable>類別，您也必須覆寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>核心以傳回您類別的新執行個體。 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 在您建立自訂 *\<Type>* KeyFrame 動畫後，您可以將它和該類型的 *\<Type>* AnimationUsingKeyFrames 搭配使用。  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>建立自訂動畫類別  
 建立您自己的動畫類型可讓您更充分掌控物件的動畫效果。 有兩個建議的方法，建立您自己的動畫類型： 您可以從衍生<xref:System.Windows.Media.Animation.AnimationTimeline>類別或*\<型別 >* AnimationBase 類別。 不建議衍生自 *\<Type>* Animation 或 *\<Type>* AnimationUsingKeyFrames 類型。  
  
### <a name="derive-from-typeanimationbase"></a>衍生自 \<Type>AnimationBase  
 衍生自 *\<Type>* AnimationBase 類別是建立新動畫類型最簡單的方式。 當您想要對已有對應 *\<Type>* AnimationBase 類別的類型建立新動畫時，使用這個方法。  
  
 **實作指示**  
  
 衍生自 *\<Type>* Animation 類別並實作 GetCurrentValueCore 方法。 GetCurrentValueCore 方法會傳回動畫目前的值。 此方法採用三個參數： 建議的起始值、 建議結束值和<xref:System.Windows.Media.Animation.AnimationClock>，用來判斷動畫進度。  
  
 因為*\<類型 >* AnimationBase 類別繼承自<xref:System.Windows.Freezable>類別，您也必須覆寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>核心以傳回您類別的新執行個體。 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 如需詳細資訊，請參閱想要以動畫顯示之類型的*\<Type>* AnimationBase 類別適用的 GetCurrentValueCore 方法文件。 如需範例，請參閱[自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **替代方法**  
  
 如果您只想要變更插入動畫值的方式，可考慮衍生自 *\<Type>* KeyFrame 類別之一。 您建立的主要畫面格可以與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的對應 *\<Type>* AnimationUsingKeyFrames 一起使用。  
  
### <a name="derive-from-animationtimeline"></a>衍生自 AnimationTimeline  
 衍生自<xref:System.Windows.Media.Animation.AnimationTimeline>類別，在您想要建立的型別，還沒有相符的動畫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫，或您想要建立動畫，並不強型別。  
  
 **實作指示**  
  
 衍生自<xref:System.Windows.Media.Animation.AnimationTimeline>類別並覆寫下列成員：  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> – 如果您的新類別是具體的您必須覆寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>傳回您類別的新執行個體。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> -覆寫此方法以傳回動畫目前的值。 此方法採用三個參數︰ 預設原始值、 預設目的值和<xref:System.Windows.Media.Animation.AnimationClock>。 使用<xref:System.Windows.Media.Animation.AnimationClock>以取得目前的時間或動畫的進度。 您可以選擇是否要使用預設的來源和目的值。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> -覆寫這個屬性，指出動畫是否使用指定的預設目的地值<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>方法。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> -覆寫這個屬性，指出<xref:System.Type>動畫所產生的輸出。  
  
 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 建議的範例 (由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫使用) 是使用兩個繼承層級︰  
  
1. 建立抽象*\<類型 >* AnimationBase 類別衍生自<xref:System.Windows.Media.Animation.AnimationTimeline>。 這個類別應該覆寫<xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>方法。 它也應該引進新的抽象方法 GetCurrentValueCore 並覆寫<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>，因此它會驗證預設原始值和預設目的值參數的類型，然後呼叫 GetCurrentValueCore。  
  
2. 建立另一個類別繼承自新*\<類型 >* AnimationBase 類別並覆寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>方法中，您引進的 GetCurrentValueCore 方法和<xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>屬性。  
  
 **替代方法**  
  
 如果您想要以動畫顯示沒有對應 From/To/By 動畫或主要畫面格動畫類型，請考慮使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>。 因為是弱型別，<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>可以動畫顯示任何類型的值。 這種方法的缺點在於<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>只支援離散插補。  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>使用每一畫面的回呼  
 當您需要完全略過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統時，使用此方法。 此方法的一個案例為物理動畫，其中的每個動畫步驟都需要根據最後一組物件互動來重新計算動畫物件的新方向或位置。  
  
 **實作指示**  
  
 和本概觀中所述的其他方法不同，若要使用每一畫面的回呼，您不需要建立自訂動畫或主要畫面格類別。  
  
 相反地，您註冊<xref:System.Windows.Media.CompositionTarget.Rendering>事件的物件，其中包含您想要以動畫顯示的物件。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合樹狀結構時，就會呼叫您的事件處理常式方法。  
  
 在事件處理常式中，執行動畫效果所需的任何計算，並使用這些值設定您想要建立動畫的物件屬性。  
  
 若要取得目前畫面的呈現時間<xref:System.EventArgs>與此相關聯事件可以轉換成<xref:System.Windows.Media.RenderingEventArgs>，這會提供<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>屬性，可用來取得目前畫面格的呈現時間。  
  
 如需詳細資訊，請參閱<xref:System.Windows.Media.CompositionTarget.Rendering>頁面。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [路徑動畫概觀](path-animations-overview.md)
- [動畫概觀](animation-overview.md)
- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)
