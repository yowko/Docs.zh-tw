---
title: 利用 UI 自動化尋找和反白顯示文字
description: 使用消費者介面自動化尋找並醒目提示文字。 一個範例會依序搜尋和反白顯示文字控制項內容內每個出現的字串。
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
ms.openlocfilehash: 7ae933bdf12c81e48371fa89ba5fc5cf5dd4731e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276460"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>利用 UI 自動化尋找和反白顯示文字

> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題將示範如何使用，以順序搜尋和反白顯示文字控制項內容中的每個出現的字串 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。  
  
## <a name="example"></a>範例  

 下列範例會 <xref:System.Windows.Automation.TextPattern> 從文字控制項取得物件。 <xref:System.Windows.Automation.Text.TextPatternRange>接著，會使用這個的屬性來建立物件（表示整份檔的文字內容） <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> <xref:System.Windows.Automation.TextPattern> 。 <xref:System.Windows.Automation.Text.TextPatternRange>接著會針對連續搜尋和醒目提示功能建立兩個額外的物件。  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>另請參閱

- [利用 UI 自動化尋找和反白顯示文字](find-and-highlight-text-using-ui-automation.md)
