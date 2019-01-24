---
title: 使用 UI 自動化取得文字屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 62abb18e9ef43e78c0e908b94f3ed9fc69861c7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512576"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>使用 UI 自動化取得文字屬性
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 從文字範圍取得文字屬性。 文字範圍可以對應至文件內目前的插入號位置 (或變質選取範圍)、連續文字選取範圍、非連續文字選取範圍的集合，或文件的整個文字內容。  
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何取得文字範圍中的 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> 。  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern> 控制項模式 (結合 <xref:System.Windows.Automation.Text.TextPatternRange> 類別) 可支援基本文字屬性 (Attribute)、屬性 (Property) 及方法。 如果是 <xref:System.Windows.Automation.TextPattern> 或 <xref:System.Windows.Automation.Text.TextPatternRange> 不支援的控制項特定功能， <xref:System.Windows.Automation.AutomationElement>類別會提供使用者介面自動化用戶端方法，以存取對應的原生物件模型。  
  
## <a name="see-also"></a>另請參閱
- [UI 自動化 TextPattern 概觀](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [使用 UI 自動化將內容新增至文字方塊](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [使用 UI 自動化尋找和反白顯示文字](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [使用 UI 自動化取得混合文字屬性詳細資料](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
