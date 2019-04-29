---
title: HOW TO：覆寫邏輯樹狀結構
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768442"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="86be4-102">HOW TO：覆寫邏輯樹狀結構</span><span class="sxs-lookup"><span data-stu-id="86be4-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="86be4-103">雖然在大部分情況下不需要這麼做，但是資深的控制項作者可以選擇覆寫邏輯樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="86be4-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86be4-104">範例</span><span class="sxs-lookup"><span data-stu-id="86be4-104">Example</span></span>  
 <span data-ttu-id="86be4-105">這個範例說明如何以子類別<xref:System.Windows.Controls.StackPanel>在此情況下覆寫邏輯樹狀結構，以強制執行的行為可能只需要面板，並只會轉譯單一子項目。</span><span class="sxs-lookup"><span data-stu-id="86be4-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="86be4-106">這不一定是實際所需的行為，而只是用來說明覆寫項目之一般邏輯樹狀結構的情節。</span><span class="sxs-lookup"><span data-stu-id="86be4-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="86be4-107">如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](trees-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="86be4-107">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>
