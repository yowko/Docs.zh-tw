---
title: 利用 UI 自動化取得混合文字屬性的詳細資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 09dbbcd4ef3bd36a4aa2578a0dc22449ab1d3dfc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201394"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="af7b5-102">利用 UI 自動化取得混合文字屬性的詳細資料</span><span class="sxs-lookup"><span data-stu-id="af7b5-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="af7b5-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="af7b5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="af7b5-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="af7b5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="af7b5-105">本主題說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ，從跨越多個屬性值的文字範圍中取得文字屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="af7b5-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="af7b5-106">文字範圍可以對應至文件內目前的插入號位置 (或變質選取範圍)、連續文字選取範圍、非連續文字選取範圍的集合，或文件的整個文字內容。</span><span class="sxs-lookup"><span data-stu-id="af7b5-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af7b5-107">範例</span><span class="sxs-lookup"><span data-stu-id="af7b5-107">Example</span></span>  
 <span data-ttu-id="af7b5-108">下列程式碼範例說明如何取得文字範圍中的 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> ，其中 <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> 會傳回 <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> 物件。</span><span class="sxs-lookup"><span data-stu-id="af7b5-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="af7b5-109"><xref:System.Windows.Automation.TextPattern> 控制項模式 (結合 <xref:System.Windows.Automation.Text.TextPatternRange> 類別) 可支援基本文字屬性 (Attribute)、屬性 (Property) 及方法。</span><span class="sxs-lookup"><span data-stu-id="af7b5-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="af7b5-110">如果是 <xref:System.Windows.Automation.TextPattern> 或 <xref:System.Windows.Automation.Text.TextPatternRange>不支援的控制項特定功能， <xref:System.Windows.Automation.AutomationElement> 類別會提供使用者介面自動化用戶端方法，以存取對應的原生物件模型。</span><span class="sxs-lookup"><span data-stu-id="af7b5-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7b5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af7b5-111">See Also</span></span>  
 [<span data-ttu-id="af7b5-112">UI 自動化 TextPattern 概觀</span><span class="sxs-lookup"><span data-stu-id="af7b5-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="af7b5-113">使用 UI 自動化將內容新增至文字方塊</span><span class="sxs-lookup"><span data-stu-id="af7b5-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="af7b5-114">使用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="af7b5-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="af7b5-115">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="af7b5-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="af7b5-116">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="af7b5-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="af7b5-117">使用 UI 自動化取得文字屬性</span><span class="sxs-lookup"><span data-stu-id="af7b5-117">Obtain Text Attributes Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
