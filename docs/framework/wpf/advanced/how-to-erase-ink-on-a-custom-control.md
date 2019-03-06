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
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="1ab8a-102">HOW TO：清除自訂控制項上的筆墨</span><span class="sxs-lookup"><span data-stu-id="1ab8a-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="1ab8a-103"><xref:System.Windows.Ink.IncrementalStrokeHitTester>判斷目前所繪製的筆劃是否與另一個筆劃交集。</span><span class="sxs-lookup"><span data-stu-id="1ab8a-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="1ab8a-104">建立控制項，可讓使用者清除筆觸的組件，這非常有用，方式上的使用者可以<xref:System.Windows.Controls.InkCanvas>時<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>設定為<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>。</span><span class="sxs-lookup"><span data-stu-id="1ab8a-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ab8a-105">範例</span><span class="sxs-lookup"><span data-stu-id="1ab8a-105">Example</span></span>  
 <span data-ttu-id="1ab8a-106">下列範例會建立自訂控制項，可讓使用者清除筆觸的部分。</span><span class="sxs-lookup"><span data-stu-id="1ab8a-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="1ab8a-107">這個範例會建立包含筆墨，初始化時的控制項。</span><span class="sxs-lookup"><span data-stu-id="1ab8a-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="1ab8a-108">若要建立會收集筆跡的控制項，請參閱[建立筆墨輸入控制項](creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab8a-108">To create a control that collects ink, see [Creating an Ink Input Control](creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
