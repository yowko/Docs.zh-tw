---
title: 如何在樣式中建立動畫（WPF）
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 617d41ca1c97463bf1c61c0d1e2728756fd8f1fb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459236"
---
# <a name="how-to-animate-in-a-style"></a>如何在樣式中建立動畫

這個範例示範如何以動畫顯示樣式中的屬性。 在樣式中建立動畫時，只有定義樣式的 framework 元素可以直接作為目標。 若要以可凍結的物件為目標，您必須從樣式專案的屬性「向下點」。

在下列範例中，會在樣式內定義數個動畫，並套用至 <xref:System.Windows.Controls.Button>。 當使用者將滑鼠指標移至按鈕上方時，會重複地從不透明漸淡到部分半透明，然後再次回復。 當使用者將滑鼠移開按鈕時，它會變成完全不透明。 當按下按鈕時，其背景色彩會從橙色變更為白色，然後再返回一次。 因為用來繪製按鈕的 <xref:System.Windows.Media.SolidColorBrush> 無法直接設為目標，所以可以從按鈕的 <xref:System.Windows.Controls.Control.Background%2A> 屬性中向下將來存取它。

## <a name="example"></a>範例

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

請注意，當您在樣式中建立動畫時，可能會以不存在的物件為目標。 例如，假設您的樣式使用 <xref:System.Windows.Media.SolidColorBrush> 來設定按鈕的 background 屬性，但在某個時間點，會覆寫樣式，而按鈕的背景則是以 <xref:System.Windows.Media.LinearGradientBrush>設定。  嘗試以動畫顯示 <xref:System.Windows.Media.SolidColorBrush> 不會擲回例外狀況;動畫只會以無訊息模式失敗。

如需有關分鏡腳本目標語法的詳細資訊，請參閱分鏡腳本[總覽](storyboards-overview.md)。 如需動畫的詳細資訊，請參閱[動畫總覽](animation-overview.md)。 如需樣式的詳細資訊，請參閱[樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。
