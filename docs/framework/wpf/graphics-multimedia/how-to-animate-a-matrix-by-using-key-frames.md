---
title: 如何：使用主要畫面格建立矩陣的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344912"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>如何：使用主要畫面格建立矩陣的動畫
此示例演示如何使用關鍵幀對<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>進行動畫處理。  
  
## <a name="example"></a>範例  
 下面的示例使用 類<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.MatrixTransform>設置<xref:System.Windows.Media.MatrixTransform.Matrix%2A>動畫。 該示例使用<xref:System.Windows.Media.MatrixTransform>物件轉換 的外觀<xref:System.Windows.Controls.Button>和位置。  
  
 此動畫使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>類創建兩個關鍵幀，並對其進行以下操作：  
  
1. 在前 0.2 秒內為第一個<xref:System.Windows.Media.Matrix>進行動畫處理。 該示例更改<xref:System.Windows.Media.Matrix.M11%2A>的<xref:System.Windows.Media.Matrix.M12%2A>和<xref:System.Windows.Media.Matrix>屬性。 此更改會導致按鈕拉伸並變得傾斜。 該示例還更改<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性，以便按鈕更改位置。  
  
2. 在 1.0 秒內為第二個<xref:System.Windows.Media.Matrix>設置動畫。 當按鈕不再傾斜或拉伸時，按鈕將移動到其他位置。  
  
3. 無限期重複動畫。  
  
> [!NOTE]
> 從<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件派生的關鍵幀在值之間創建突然跳轉，也就是說，動畫的移動是抖動的。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [關於主要畫面格操作說明的主題](key-frame-animation-how-to-topics.md)
