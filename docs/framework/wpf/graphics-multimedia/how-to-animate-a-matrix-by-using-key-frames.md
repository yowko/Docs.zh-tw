---
title: 如何：使用主要畫面格建立矩陣的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 8f58b43a870f2c85ae4349965f586a33e2f75a2a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485846"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>如何：使用主要畫面格建立矩陣的動畫
此範例示範如何建立動畫<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。 此範例會使用<xref:System.Windows.Media.MatrixTransform>要轉換的外觀和位置物件<xref:System.Windows.Controls.Button>。  
  
 這個動畫使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>建立兩個主要畫面格類別，並會與其進行下列作業：  
  
1.  以動畫顯示的第一個<xref:System.Windows.Media.Matrix>前 0.2 秒的期間。 範例會變更<xref:System.Windows.Media.Matrix.M11%2A>並<xref:System.Windows.Media.Matrix.M12%2A>的屬性<xref:System.Windows.Media.Matrix>。 這項變更會使按鈕自動縮放，並會扭曲。 此範例也會變更<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性，讓按鈕變更位置。  
  
2.  以動畫顯示第二個<xref:System.Windows.Media.Matrix>1.0 秒時。 按鈕會移至另一個位置，而不會再扭曲或自動縮放 按鈕。  
  
3.  無限期地重複動畫。  
  
> [!NOTE]
>  主要畫面衍生自<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件建立突然跳躍點之間的值，亦即動畫的移動會不穩定。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
