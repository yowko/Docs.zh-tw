---
title: 如何：覆寫邏輯樹狀結構
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542886"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="08ac7-102">如何：覆寫邏輯樹狀結構</span><span class="sxs-lookup"><span data-stu-id="08ac7-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="08ac7-103">雖然在大部分情況下不需要這麼做，但是資深的控制項作者可以選擇覆寫邏輯樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="08ac7-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ac7-104">範例</span><span class="sxs-lookup"><span data-stu-id="08ac7-104">Example</span></span>  
 <span data-ttu-id="08ac7-105">這個範例說明如何以子類別<xref:System.Windows.Controls.StackPanel>若要在此情況下覆寫邏輯樹狀結構，以強制執行行為可能只有面板，並只會呈現單一子項目。</span><span class="sxs-lookup"><span data-stu-id="08ac7-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="08ac7-106">這不一定是實際所需的行為，而只是用來說明覆寫項目之一般邏輯樹狀結構的情節。</span><span class="sxs-lookup"><span data-stu-id="08ac7-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="08ac7-107">如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="08ac7-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
