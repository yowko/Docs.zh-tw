---
title: "如何：使用主要畫面格建立矩陣的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c67b5c8e179485083a40aa8a196fbee3e0fc24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>如何：使用主要畫面格建立矩陣的動畫
此範例示範如何以動畫方式顯示<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>所使用的主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。 此範例會使用<xref:System.Windows.Media.MatrixTransform>要轉換的外觀和位置物件<xref:System.Windows.Controls.Button>。  
  
 這個動畫使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>類別來建立兩個主要畫面格，並會與其下列：  
  
1.  以動畫方式顯示第一個<xref:System.Windows.Media.Matrix>的第一個 0.2 秒數內。 範例會變更<xref:System.Windows.Media.Matrix.M11%2A>和<xref:System.Windows.Media.Matrix.M12%2A>屬性<xref:System.Windows.Media.Matrix>。 這項變更會使按鈕自動縮放，並會扭曲。 此範例也會變更<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性，讓按鈕將變更位置。  
  
2.  以動畫方式顯示第二個<xref:System.Windows.Media.Matrix>在 1.0 秒。 雖然不會再扭曲或自動縮放 按鈕，按鈕會移到另一個位置。  
  
3.  無限期地重複動畫。  
  
> [!NOTE]
>  主要畫面衍生自<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件建立值之間的突然跳躍點，也就是不穩定的動畫移動。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
