---
title: "如何：辨認應用程式筆勢"
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
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdff97fdb48126f3a7b970c677cf96f9c2ddaf8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="80424-102">如何：辨認應用程式筆勢</span><span class="sxs-lookup"><span data-stu-id="80424-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="80424-103">下列範例示範如何清除筆墨，當使用者<xref:System.Windows.Ink.ApplicationGesture.ScratchOut>軌跡上<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="80424-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="80424-104">這個範例假設<xref:System.Windows.Controls.InkCanvas>，稱為`inkCanvas1`，XAML 檔中宣告。</span><span class="sxs-lookup"><span data-stu-id="80424-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80424-105">範例</span><span class="sxs-lookup"><span data-stu-id="80424-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="80424-106">請參閱</span><span class="sxs-lookup"><span data-stu-id="80424-106">See Also</span></span>  
 <xref:System.Windows.Ink.ApplicationGesture>  
 <xref:System.Windows.Controls.InkCanvas>  
 <xref:System.Windows.Controls.InkCanvas.Gesture>
