---
title: HOW TO：清除自訂控制項上的筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365889"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>HOW TO：清除自訂控制項上的筆墨
<xref:System.Windows.Ink.IncrementalStrokeHitTester>判斷目前所繪製的筆劃是否與另一個筆劃交集。  建立控制項，可讓使用者清除筆觸的組件，這非常有用，方式上的使用者可以<xref:System.Windows.Controls.InkCanvas>時<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>設定為<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>。  
  
## <a name="example"></a>範例  
 下列範例會建立自訂控制項，可讓使用者清除筆觸的部分。  這個範例會建立包含筆墨，初始化時的控制項。  若要建立會收集筆跡的控制項，請參閱[建立筆墨輸入控制項](creating-an-ink-input-control.md)。  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
