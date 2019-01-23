---
title: 如何：辨認應用程式筆勢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 68a7c8cd4b8ed935d005fabff37a7b44c1b98012
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506702"
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="e91e2-102">如何：辨認應用程式筆勢</span><span class="sxs-lookup"><span data-stu-id="e91e2-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="e91e2-103">下列範例示範如何清除的筆墨，當使用者提出<xref:System.Windows.Ink.ApplicationGesture.ScratchOut>軌跡上<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="e91e2-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="e91e2-104">這個範例假設<xref:System.Windows.Controls.InkCanvas>，稱為`inkCanvas1`，在 XAML 檔案中宣告。</span><span class="sxs-lookup"><span data-stu-id="e91e2-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e91e2-105">範例</span><span class="sxs-lookup"><span data-stu-id="e91e2-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e91e2-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e91e2-106">See also</span></span>
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
