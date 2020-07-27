---
title: 利用 UI 自動化公開資料表的內容
description: 請參閱如何使用 UI 自動化公開資料表的內容。 表格式控制項中每個資料格的內容和內建屬性會公開。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: c6ceb05421547a7e84f612ed6da2bd7002bf095b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168459"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a><span data-ttu-id="0ec51-104">利用 UI 自動化公開資料表的內容</span><span class="sxs-lookup"><span data-stu-id="0ec51-104">Expose the Content of a Table Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="0ec51-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="0ec51-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0ec51-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="0ec51-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0ec51-107">本主題說明如何 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 使用來公開表格式控制項中每個資料格的內容和內部屬性。</span><span class="sxs-lookup"><span data-stu-id="0ec51-107">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose the content and intrinsic properties of each cell within a tabular control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ec51-108">範例</span><span class="sxs-lookup"><span data-stu-id="0ec51-108">Example</span></span>  
 <span data-ttu-id="0ec51-109">下列程式碼範例將示範如何取得 <xref:System.Windows.Automation.AutomationElement> 代表資料表單元格內容的，也會取得資料列和資料行索引、資料列和資料行的範圍等儲存格屬性。</span><span class="sxs-lookup"><span data-stu-id="0ec51-109">The following code example demonstrates how to obtain a <xref:System.Windows.Automation.AutomationElement> that represents the content of a table cell; cell properties such as row and column indices, row and column spans, and row and column header information are also obtained.</span></span> <span data-ttu-id="0ec51-110">這個範例會使用焦點變更事件處理常式，來模擬執行之表格式控制項的鍵盤遍歷 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0ec51-110">This example uses a focus change event handler to simulate keyboard traversal of a tabular control that implements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="0ec51-111">每個資料表專案的資訊會在焦點變更事件上公開。</span><span class="sxs-lookup"><span data-stu-id="0ec51-111">Information for each table item is exposed on a focus change event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ec51-112">由於焦點變更是全域桌面事件，因此應該篩選資料表外部的焦點變更事件。</span><span class="sxs-lookup"><span data-stu-id="0ec51-112">Since focus changes are global desktop events, focus change events outside the table should be filtered.</span></span> <span data-ttu-id="0ec51-113">如需相關的執行方式，請參閱[TrackFocus 範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="0ec51-113">See the [TrackFocus Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) for a related implementation.</span></span>  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="0ec51-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec51-114">See also</span></span>

- [<span data-ttu-id="0ec51-115">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="0ec51-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0ec51-116">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="0ec51-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0ec51-117">實作 UI 自動化 Table 控制項模式</span><span class="sxs-lookup"><span data-stu-id="0ec51-117">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="0ec51-118">實作 UI 自動化 TableItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="0ec51-118">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="0ec51-119">實作 UI 自動化 Grid 控制項模式</span><span class="sxs-lookup"><span data-stu-id="0ec51-119">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="0ec51-120">實作 UI 自動化 GridItem 控制項模式</span><span class="sxs-lookup"><span data-stu-id="0ec51-120">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
