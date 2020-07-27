---
title: 使用 UI 自動化將內容加入至文字方塊
description: 請參閱範例，以瞭解如何在 .NET 中使用 Microsoft UI 自動化，將內容新增至單一行文字方塊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 4136d460de7091a515580cade16f06e54699727a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166908"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="f48c6-103">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="f48c6-103">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="f48c6-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="f48c6-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f48c6-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f48c6-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f48c6-106">本主題包含範例程式碼，示範如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 將文字插入單行文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f48c6-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="f48c6-107">另一種方法是針對不適用的多行和 rtf 文字控制項提供 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f48c6-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="f48c6-108">為了進行比較，此範例也會示範如何使用 Win32 方法來完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="f48c6-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f48c6-109">範例</span><span class="sxs-lookup"><span data-stu-id="f48c6-109">Example</span></span>  
 <span data-ttu-id="f48c6-110">下列範例會逐步解說目標應用程式中的一連串文字控制項。</span><span class="sxs-lookup"><span data-stu-id="f48c6-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="f48c6-111">測試每個文字控制項，以查看是否 <xref:System.Windows.Automation.ValuePattern> 可以使用方法從它取得物件 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f48c6-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="f48c6-112">如果文字控制項支援 <xref:System.Windows.Automation.ValuePattern> ，則 <xref:System.Windows.Automation.ValuePattern.SetValue%2A> 會使用方法將使用者定義的字串插入至文字控制項。</span><span class="sxs-lookup"><span data-stu-id="f48c6-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="f48c6-113">否則， <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> 會使用方法。</span><span class="sxs-lookup"><span data-stu-id="f48c6-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="f48c6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f48c6-114">See also</span></span>

- <span data-ttu-id="f48c6-115">[TextPattern 插入文字範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f48c6-115">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
