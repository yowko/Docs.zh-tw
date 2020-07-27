---
title: 利用 UI 自動化尋找和反白顯示文字
description: 使用使用者介面自動化尋找和反白顯示文字。 一個範例會依序搜尋並反白顯示文字控制項內容中每個出現的字串。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: e4aca4b5ccdbc429a3d6267afc09b9f8b99cd7e9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164203"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="7558c-104">利用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="7558c-104">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="7558c-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="7558c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7558c-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="7558c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7558c-107">本主題示範如何使用在文字控制項的內容中，依序搜尋和反白顯示每個出現的字串 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7558c-107">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="7558c-108">範例</span><span class="sxs-lookup"><span data-stu-id="7558c-108">Example</span></span>  
 <span data-ttu-id="7558c-109">下列範例會 <xref:System.Windows.Automation.TextPattern> 從文字控制項取得物件。</span><span class="sxs-lookup"><span data-stu-id="7558c-109">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="7558c-110"><xref:System.Windows.Automation.Text.TextPatternRange>接著，代表整個檔之文字內容的物件，會使用 <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> 這個的屬性來建立 <xref:System.Windows.Automation.TextPattern> 。</span><span class="sxs-lookup"><span data-stu-id="7558c-110">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="7558c-111"><xref:System.Windows.Automation.Text.TextPatternRange>接著會針對順序搜尋和反白顯示功能建立兩個額外的物件。</span><span class="sxs-lookup"><span data-stu-id="7558c-111">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="7558c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7558c-112">See also</span></span>

- [<span data-ttu-id="7558c-113">利用 UI 自動化尋找和反白顯示文字</span><span class="sxs-lookup"><span data-stu-id="7558c-113">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
