---
title: "如何：清除自訂控制項上的筆墨"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23d234d97d6b25394df87016f0671d86b10a2853
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>如何：清除自訂控制項上的筆墨
<xref:System.Windows.Ink.IncrementalStrokeHitTester>決定目前繪製的筆劃是否與另一個筆觸有交集。  建立控制項可讓使用者清除筆觸的組件，這非常有用，方式上的使用者可以<xref:System.Windows.Controls.InkCanvas>時<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>設<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>。  
  
## <a name="example"></a>範例  
 下列範例會建立可讓使用者清除筆觸的組件的自訂控制項。  這個範例會建立包含筆墨會在初始化時的控制項。  若要建立會收集筆墨的控制項，請參閱[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
