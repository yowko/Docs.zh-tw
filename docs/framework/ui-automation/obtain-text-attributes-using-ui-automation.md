---
title: 使用 UI 自動化取得文字屬性
description: 瞭解如何使用使用者介面自動化來取得文字屬性。 請參閱從文字範圍取得文字屬性的程式碼範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: b48f773e27088ba4b33ad01b299d77a0992a9159
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168009"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="bf745-104">使用 UI 自動化取得文字屬性</span><span class="sxs-lookup"><span data-stu-id="bf745-104">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="bf745-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="bf745-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bf745-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="bf745-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bf745-107">本主題說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 從文字範圍取得文字屬性。</span><span class="sxs-lookup"><span data-stu-id="bf745-107">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="bf745-108">文字範圍可以對應至文件內目前的插入號位置 (或變質選取範圍)、連續文字選取範圍、非連續文字選取範圍的集合，或文件的整個文字內容。</span><span class="sxs-lookup"><span data-stu-id="bf745-108">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf745-109">範例</span><span class="sxs-lookup"><span data-stu-id="bf745-109">Example</span></span>  
 <span data-ttu-id="bf745-110">下列程式碼範例說明如何取得文字範圍中的 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="bf745-110">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="bf745-111"><xref:System.Windows.Automation.TextPattern> 控制項模式 (結合 <xref:System.Windows.Automation.Text.TextPatternRange> 類別) 可支援基本文字屬性 (Attribute)、屬性 (Property) 及方法。</span><span class="sxs-lookup"><span data-stu-id="bf745-111">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="bf745-112">如果是 <xref:System.Windows.Automation.TextPattern> 或 <xref:System.Windows.Automation.Text.TextPatternRange> 不支援的控制項特定功能， <xref:System.Windows.Automation.AutomationElement>類別會提供使用者介面自動化用戶端方法，以存取對應的原生物件模型。</span><span class="sxs-lookup"><span data-stu-id="bf745-112">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf745-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf745-113">See also</span></span>

- [<span data-ttu-id="bf745-114">UI 自動化 TextPattern 概觀</span><span class="sxs-lookup"><span data-stu-id="bf745-114">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="bf745-115">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="bf745-115">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="bf745-116">利用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="bf745-116">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="bf745-117">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="bf745-117">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bf745-118">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="bf745-118">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bf745-119">利用 UI 自動化取得混合文字屬性的詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf745-119">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](obtain-mixed-text-attribute-details-using-ui-automation.md)
