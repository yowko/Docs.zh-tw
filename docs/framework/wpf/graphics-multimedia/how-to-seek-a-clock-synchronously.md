---
title: HOW TO：同步搜尋時鐘
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
ms.openlocfilehash: 9b6b1f5523effc56ccd9ddaa4f478e1d3a20ada8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651255"
---
# <a name="how-to-seek-a-clock-synchronously"></a>HOW TO：同步搜尋時鐘
使用<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>同步搜尋時鐘的特定點的方法。 下列範例示範兩者<xref:System.Windows.Media.Animation.ClockController.Seek%2A>並<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>方法<xref:System.Windows.Media.Animation.ClockController>。  
  
 此範例示範如何搜尋<xref:System.Windows.Media.Animation.Clock>; 如需示範如何尋找分鏡腳本，請參閱範例[分鏡腳本同步搜尋](how-to-seek-a-storyboard-synchronously.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](~/samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
