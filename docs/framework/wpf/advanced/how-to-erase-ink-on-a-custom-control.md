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
ms.workload: dotnet
ms.openlocfilehash: e05163bcbafd360e0929fe784ff1111bd0663ef3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="793eb-102">如何：清除自訂控制項上的筆墨</span><span class="sxs-lookup"><span data-stu-id="793eb-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="793eb-103"><xref:System.Windows.Ink.IncrementalStrokeHitTester>決定目前繪製的筆劃是否與另一個筆觸有交集。</span><span class="sxs-lookup"><span data-stu-id="793eb-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="793eb-104">建立控制項可讓使用者清除筆觸的組件，這非常有用，方式上的使用者可以<xref:System.Windows.Controls.InkCanvas>時<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>設<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>。</span><span class="sxs-lookup"><span data-stu-id="793eb-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="793eb-105">範例</span><span class="sxs-lookup"><span data-stu-id="793eb-105">Example</span></span>  
 <span data-ttu-id="793eb-106">下列範例會建立可讓使用者清除筆觸的組件的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="793eb-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="793eb-107">這個範例會建立包含筆墨會在初始化時的控制項。</span><span class="sxs-lookup"><span data-stu-id="793eb-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="793eb-108">若要建立會收集筆墨的控制項，請參閱[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="793eb-108">To create a control that collects ink, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
