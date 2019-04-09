---
title: HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170647"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制
此範例示範如何控制<xref:System.Windows.Media.Animation.Storyboard>啟動之後。 若要啟動<xref:System.Windows.Media.Animation.Storyboard>利用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Media.Animation.BeginStoryboard>，這會對物件和屬性，它們建立動畫，然後啟動 分鏡腳本將動畫的散發。 如果您賦予<xref:System.Windows.Media.Animation.BeginStoryboard>藉由指定的名稱及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性，讓它可控制的分鏡腳本。 然後您可以以互動方式控制分鏡腳本開始後。  
  
 使用下列的分鏡腳本動作，並搭配<xref:System.Windows.EventTrigger>物件來控制分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>:暫停分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>:繼續已暫停的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:變更分鏡腳本的速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:如果有的話，請前進到其填滿期間中，結尾的分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>:停止分鏡腳本。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>:移除分鏡腳本，釋放資源。  
  
## <a name="example"></a>範例  
 下列範例會使用可控制的分鏡腳本動作以互動方式控制分鏡腳本。  
  
 **注意：** 若要查看使用程式碼來控制分鏡腳本的範例，請參閱[控制分鏡腳本之後它會開始使用其互動方法](how-to-control-a-storyboard-after-it-starts.md)。  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 如需其他範例，請參閱 <<c0> [ 動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [在分鏡腳本開始後，使用其互動方法來進行控制](how-to-control-a-storyboard-after-it-starts.md)
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
