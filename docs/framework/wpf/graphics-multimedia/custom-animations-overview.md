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
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186555"
---
# <a name="custom-animations-overview"></a>自訂動畫概觀
本主題說明如何以及何時建立自訂主要畫面格、動畫類別來擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統，或使用每一畫面的回呼來略過它。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的不同動畫類型。 如需詳細資訊，請參閱＜From/To/By 動畫概觀＞、[主要畫面格動畫概觀](key-frame-animations-overview.md)以及[路徑動畫概觀](path-animations-overview.md)。  
  
 由於動畫類從<xref:System.Windows.Freezable>類繼承，因此應熟悉<xref:System.Windows.Freezable>物件以及如何從<xref:System.Windows.Freezable>繼承。 如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>擴充動畫系統  
 有數種方式可以擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統，根據您想要使用的內建功能層級而定。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎中有三個主要擴充點︰  
  
- 通過從*\<類型>* KeyFrame 類之一（如<xref:System.Windows.Media.Animation.DoubleKeyFrame>）繼承來創建自訂關鍵幀物件。 這個方法可使用大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎內建功能。  
  
- 通過繼承或<xref:System.Windows.Media.Animation.AnimationTimeline>從*\<類型>* 動畫基礎類之一創建自己的動畫類。  
  
- 您可以針對每一畫面格使用每一畫面的回呼來產生動畫。 這個方法完全略過動畫與計時系統。  
  
 下表說明一些擴充動畫系統的案例。  
  
|當您要...|使用這個方法|  
|-------------------------|-----------------------|  
|自訂具有相應*\<類型>* 動畫使用關鍵幀的類型的值之間的插值|建立自訂主要畫面格。 如需詳細資訊，請參閱[建立自訂主要畫面格](#createacustomkeyframe)一節。|  
|自訂的不僅僅是具有相應*\<類型>* 動畫的類型的值之間的插值。|創建從*\<類型>* 動畫基礎類繼承的自訂動畫類，該類對應于要設置動畫的類型。 如需詳細資訊，請參閱[建立自訂動畫類別](#createacustomanimationtype)一節。|  
|以動畫顯示沒有對應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類型的動畫|使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>或 創建從<xref:System.Windows.Media.Animation.AnimationTimeline>繼承的類。 如需詳細資訊，請參閱[建立自訂動畫類別](#createacustomanimationtype)一節。|  
|利用每個畫面格都會計算的值，並根據最後一組物件互動的值，以動畫顯示多個物件|使用每一畫面的回呼。 如需詳細資訊，請參閱[使用每一畫面的回呼](#useperframecallback)一節。|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>建立自訂主要畫面格  
 建立自訂主要畫面格類別是擴充動畫系統最簡單的方式。 當您想要不同的主要畫面格動畫內插補點方法時，請使用這個方法。  如[主要畫面格動畫概觀](key-frame-animations-overview.md)中所述，主要畫面格動畫使用主要畫面格物件來產生其輸出值。 每個主要畫面格物件都會執行三個函式︰  
  
- 使用其<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>屬性指定目標值。  
  
- 指定應使用其<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性達到該值的時間。  
  
- 藉由實作 InterpolateValueCore 方法，在前一個主要畫面格與其自身的值之間插入。  
  
 **實作指示**  
  
 派生自*\<類型>* KeyFrame 抽象類別，並實現插值ValueCore方法。 InterpolateValueCore 方法會傳回主要畫面格目前的值。 它接受兩個參數︰前一個主要畫面格的值和範圍從 0 到 1 的進度值。 進度 0 表示關鍵幀剛剛啟動，值 1 表示關鍵幀剛剛完成，應返回其<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>屬性指定的值。  
  
 由於*\<類型>* KeyFrame 類從<xref:System.Windows.Freezable>類繼承，因此還必須重寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>內核才能返回類的新實例。 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 創建自訂*\<類型>* KeyFrame 動畫後，可以將該類型>動畫使用關鍵幀*\<的類型*用於該類型。  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>建立自訂動畫類別  
 建立您自己的動畫類型可讓您更充分掌控物件的動畫效果。 有兩種建議的方法可以創建自己的動畫類型：可以從<xref:System.Windows.Media.Animation.AnimationTimeline>類派生*\<>* 動畫基礎類。 不建議從*\<"動畫類型>"* 或*\<"動畫>類型*>動畫使用關鍵幀類派生。  
  
### <a name="derive-from-typeanimationbase"></a>衍生自 \<Type>AnimationBase  
 從*\<類型>* 動畫基礎類派生是創建新動畫類型的最簡單方法。 如果要為已具有相應*\<類型>* 動畫基礎類的類型創建新動畫，請使用此方法。  
  
 **實作指示**  
  
 派生自*\<>* 動畫類，並實現 GetCurrentValueCore 方法。 GetCurrentValueCore 方法會傳回動畫目前的值。 它需要三個參數：建議的起始值、建議的結束值和 用於<xref:System.Windows.Media.Animation.AnimationClock>確定動畫進度的 參數。  
  
 由於*\<類型>* 動畫基礎類從<xref:System.Windows.Freezable>類繼承，因此還必須重寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>核心才能返回類的新實例。 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 有關詳細資訊，請參閱要設置動畫*\<的類型>* 動畫基礎類的 GetCurrentValueCore 方法文檔。 如需範例，請參閱[自訂動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **替代方法**  
  
 如果只想更改動畫值的插值方式，則考慮派生自*\<類型>* KeyFrame 類之一。 您創建的關鍵幀可與提供的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]相應*\<類型>* 動畫使用關鍵幀一起使用。  
  
### <a name="derive-from-animationtimeline"></a>衍生自 AnimationTimeline  
 如果要為尚未<xref:System.Windows.Media.Animation.AnimationTimeline>具有匹配[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫的類型創建動畫，或者希望創建未強型別類型的動畫，則從類派生。  
  
 **實作指示**  
  
 派生自類<xref:System.Windows.Media.Animation.AnimationTimeline>並重寫以下成員：  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>• 如果新類是具體的，則必須重寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>才能返回類的新實例。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>• 重寫此方法以返回動畫的當前值。 它需要三個參數：預設原點值、預設目標值和<xref:System.Windows.Media.Animation.AnimationClock>。 使用<xref:System.Windows.Media.Animation.AnimationClock>獲取動畫的目前時間或進度。 您可以選擇是否要使用預設的來源和目的值。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>• 重寫此屬性以指示動畫是否使用<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>方法指定的預設目標值。  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>• 重寫此屬性以指示<xref:System.Type>動畫生成的輸出。  
  
 如果類別不使用相依性屬性來儲存其資料或需要在建立之後額外進行初始化，您可能需要覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
 建議的範例 (由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫使用) 是使用兩個繼承層級︰  
  
1. 創建派生自<xref:System.Windows.Media.Animation.AnimationTimeline>的抽象*\<類型>* 動畫基礎類。 類應重寫 方法<xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>。 它還應引入一種新的抽象方法 GetCurrentValueCore 和重寫<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>，以便驗證預設原點值和預設目標值參數的類型，然後調用 GetCurrentValueCore。  
  
2. 創建從新*\<類型>* 動畫基礎類繼承的另一個類，並重寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>方法、引入的 GetCurrentValueCore 方法和<xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>屬性。  
  
 **替代方法**  
  
 如果要為沒有相應"從/到/由"動畫或關鍵幀動畫的類型設置動畫，請考慮使用<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>。 由於類型較弱，因此<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>可以為任何類型的值設置動畫。 此方法的缺點是<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>僅支援離散插值。  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>使用每一畫面的回呼  
 當您需要完全略過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統時，使用此方法。 此方法的一個案例為物理動畫，其中的每個動畫步驟都需要根據最後一組物件互動來重新計算動畫物件的新方向或位置。  
  
 **實作指示**  
  
 和本概觀中所述的其他方法不同，若要使用每一畫面的回呼，您不需要建立自訂動畫或主要畫面格類別。  
  
 相反，您可以註冊包含要<xref:System.Windows.Media.CompositionTarget.Rendering>設置動畫的物件的物件的事件。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合樹狀結構時，就會呼叫您的事件處理常式方法。  
  
 在事件處理常式中，執行動畫效果所需的任何計算，並使用這些值設定您想要建立動畫的物件屬性。  
  
 要獲取當前幀的表示時間，<xref:System.EventArgs>與此事件關聯的可以強制轉換為<xref:System.Windows.Media.RenderingEventArgs>，該<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>屬性可用於獲取當前幀的渲染時間。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Media.CompositionTarget.Rendering> 頁面。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [路徑動畫概觀](path-animations-overview.md)
- [動畫概觀](animation-overview.md)
- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [自訂動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
