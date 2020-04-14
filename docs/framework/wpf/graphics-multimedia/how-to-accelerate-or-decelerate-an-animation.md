---
title: 如何：動畫加速或減速
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 7ab55ba44b866a992b9021284f170858f0108d15
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243007"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>如何:加速或減速動畫

此示例演示如何使動畫隨著時間的推移加速和減速。 在下面的示例中,幾個矩形由具有不同<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A><xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>和設置的動畫進行動畫處理。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 此示例中省略了代碼。 有關完整代碼,請參閱[動畫計時行為 (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp)或[動畫計時行為 (視覺基本)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)。
