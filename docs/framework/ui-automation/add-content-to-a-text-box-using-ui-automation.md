---
title: 使用 UI 自動化將內容加入至文字方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932643"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="4871c-102">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="4871c-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="4871c-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="4871c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4871c-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="4871c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4871c-105">本主題包含範例程式碼, 示範如何使用[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]將文字插入單行文字方塊。</span><span class="sxs-lookup"><span data-stu-id="4871c-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="4871c-106">另一種方法是針對不適用的多行和 rtf 文字[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]控制項提供。</span><span class="sxs-lookup"><span data-stu-id="4871c-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="4871c-107">為了進行比較, 此範例也會示範如何使用 Win32 方法來完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="4871c-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4871c-108">範例</span><span class="sxs-lookup"><span data-stu-id="4871c-108">Example</span></span>  
 <span data-ttu-id="4871c-109">下列範例會逐步解說目標應用程式中的一連串文字控制項。</span><span class="sxs-lookup"><span data-stu-id="4871c-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="4871c-110">測試每個文字控制項, 以查看是否<xref:System.Windows.Automation.ValuePattern>可以<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>使用方法從它取得物件。</span><span class="sxs-lookup"><span data-stu-id="4871c-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="4871c-111">如果文字控制項支援<xref:System.Windows.Automation.ValuePattern>, 則<xref:System.Windows.Automation.ValuePattern.SetValue%2A>會使用方法將使用者定義的字串插入至文字控制項。</span><span class="sxs-lookup"><span data-stu-id="4871c-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="4871c-112">否則, <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>會使用方法。</span><span class="sxs-lookup"><span data-stu-id="4871c-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="4871c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4871c-113">See also</span></span>

- <span data-ttu-id="4871c-114">[TextPattern 插入文字範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4871c-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
