---
title: 如何：同步搜尋時鐘
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
ms.openlocfilehash: d8e7b0f4bfa3a59814d87bfb6d7e8b40bd80f6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-seek-a-clock-synchronously"></a>如何：同步搜尋時鐘
使用<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>来搜尋的特定點的時鐘同步的方法。 下列範例示範<xref:System.Windows.Media.Animation.ClockController.Seek%2A>和<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>方法<xref:System.Windows.Media.Animation.ClockController>。  
  
 這個範例示範如何搜尋<xref:System.Windows.Media.Animation.Clock>; 如需範例示範如何搜尋分鏡腳本，請參閱[分鏡腳本以同步方式搜尋](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
