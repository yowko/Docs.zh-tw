---
title: 利用 UI 自動化取得混合文字屬性的詳細資料
description: 使用 .NET API 的 system.servicemodel 命名空間中的受控使用者介面自動化類別，取得混合文字屬性的詳細資料。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 111d110be9365c4a58f2bd2b033c1ff4e3a6a95d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903853"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="e94b9-103">利用 UI 自動化取得混合文字屬性的詳細資料</span><span class="sxs-lookup"><span data-stu-id="e94b9-103">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="e94b9-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="e94b9-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e94b9-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="e94b9-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e94b9-106">本主題說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ，從跨越多個屬性值的文字範圍中取得文字屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e94b9-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="e94b9-107">文字範圍可以對應至文件內目前的插入號位置 (或變質選取範圍)、連續文字選取範圍、非連續文字選取範圍的集合，或文件的整個文字內容。</span><span class="sxs-lookup"><span data-stu-id="e94b9-107">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e94b9-108">範例</span><span class="sxs-lookup"><span data-stu-id="e94b9-108">Example</span></span>  
 <span data-ttu-id="e94b9-109">下列程式碼範例說明如何取得文字範圍中的 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> ，其中 <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> 會傳回 <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> 物件。</span><span class="sxs-lookup"><span data-stu-id="e94b9-109">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="e94b9-110"><xref:System.Windows.Automation.TextPattern> 控制項模式 (結合 <xref:System.Windows.Automation.Text.TextPatternRange> 類別) 可支援基本文字屬性 (Attribute)、屬性 (Property) 及方法。</span><span class="sxs-lookup"><span data-stu-id="e94b9-110">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="e94b9-111">如果是 <xref:System.Windows.Automation.TextPattern> 或 <xref:System.Windows.Automation.Text.TextPatternRange>不支援的控制項特定功能， <xref:System.Windows.Automation.AutomationElement> 類別會提供使用者介面自動化用戶端方法，以存取對應的原生物件模型。</span><span class="sxs-lookup"><span data-stu-id="e94b9-111">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94b9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e94b9-112">See also</span></span>

- [<span data-ttu-id="e94b9-113">UI 自動化 TextPattern 概觀</span><span class="sxs-lookup"><span data-stu-id="e94b9-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="e94b9-114">使用 UI 自動化將內容加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="e94b9-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="e94b9-115">使用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="e94b9-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="e94b9-116">UI Automation Control Patterns Overview</span><span class="sxs-lookup"><span data-stu-id="e94b9-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e94b9-117">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="e94b9-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e94b9-118">使用 UI 自動化取得文字屬性</span><span class="sxs-lookup"><span data-stu-id="e94b9-118">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
