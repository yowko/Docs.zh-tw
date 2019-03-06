---
title: 如何以動畫顯示樣式 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 5fb18a2d927746c3437ec01d2a19327be373cae3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373955"
---
# <a name="how-to-animate-in-a-style"></a>如何在樣式中建立動畫

此範例示範如何以動畫顯示樣式內的屬性。 當動畫樣式內，可以直接當做目標只有架構元素可定義樣式。 若要以 freezable 物件為目標，您必須 「 點向下 」 從該樣式的元素的屬性。

在下列範例中，數個動畫的定義於樣式中，並套用至<xref:System.Windows.Controls.Button>。 當使用者將滑鼠移至按鈕時，它會逐漸淡化的不透明為半透明再後重複。 當使用者移出按鈕的滑鼠時，它會變成完全不透明。 按一下按鈕時，則會在從橙色到白色，並再次變更它的背景色彩。 因為<xref:System.Windows.Media.SolidColorBrush>用來繪製按鈕無法直接作為目標，存取從按鈕的向下將<xref:System.Windows.Controls.Control.Background%2A>屬性。

## <a name="example"></a>範例

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

請注意，當動畫樣式內，它可能不存在的目標物件。 例如，假設會使用您的風格<xref:System.Windows.Media.SolidColorBrush>來設定按鈕的 background 屬性，但在某處的樣式會覆寫，並設定按鈕的背景<xref:System.Windows.Media.LinearGradientBrush>。  嘗試以動畫顯示<xref:System.Windows.Media.SolidColorBrush>不會擲回例外狀況; 動畫將會以無訊息模式失敗。

如需有關分鏡腳本目標語法的詳細資訊，請參閱 <<c0> [ 分鏡腳本概觀](storyboards-overview.md)。 如需動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。 如需有關樣式的詳細資訊，請參閱 <<c0> [ 設定樣式和範本](../controls/styling-and-templating.md)。
