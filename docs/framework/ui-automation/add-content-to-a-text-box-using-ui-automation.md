---
title: "使用 UI 自動化將內容加入至文字方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: edc11040a782151af83cb9318ab424426c712e0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="6b393-102">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="6b393-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="6b393-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="6b393-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6b393-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="6b393-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6b393-105">本主題包含範例程式碼，示範如何使用[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]插入單行文字方塊的文字。</span><span class="sxs-lookup"><span data-stu-id="6b393-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="6b393-106">替代方法針對多行以及 rtf 文字控制項提供其中[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不適用。</span><span class="sxs-lookup"><span data-stu-id="6b393-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="6b393-107">為了進行比較，此範例也示範如何使用 Win32 方法來完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6b393-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b393-108">範例</span><span class="sxs-lookup"><span data-stu-id="6b393-108">Example</span></span>  
 <span data-ttu-id="6b393-109">下列範例會逐一一連串的目標應用程式中的文字控制項。</span><span class="sxs-lookup"><span data-stu-id="6b393-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="6b393-110">每個文字控制項測試是否<xref:System.Windows.Automation.ValuePattern>物件可從使用它來取得<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6b393-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="6b393-111">如果文字控制項不支援<xref:System.Windows.Automation.ValuePattern>、<xref:System.Windows.Automation.ValuePattern.SetValue%2A>方法用來插入文字控制項是使用者定義的字串。</span><span class="sxs-lookup"><span data-stu-id="6b393-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="6b393-112">否則，<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>使用方法。</span><span class="sxs-lookup"><span data-stu-id="6b393-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="6b393-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b393-113">See Also</span></span>  
 [<span data-ttu-id="6b393-114">TextPattern 插入文字範例</span><span class="sxs-lookup"><span data-stu-id="6b393-114">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
