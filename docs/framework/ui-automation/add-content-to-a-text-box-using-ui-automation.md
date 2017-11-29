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
ms.openlocfilehash: 0acd6510e6349917b38e33e487123a118c2e653c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>使用 UI 自動化將內容加入至文字方塊
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，示範如何使用[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]插入單行文字方塊的文字。 替代方法針對多行以及 rtf 文字控制項提供其中[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不適用。 為了進行比較，此範例也示範如何使用 Win32 方法來完成相同的結果。  
  
## <a name="example"></a>範例  
 下列範例會逐一一連串的目標應用程式中的文字控制項。 每個文字控制項測試是否<xref:System.Windows.Automation.ValuePattern>物件可從使用它來取得<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>方法。 如果文字控制項不支援<xref:System.Windows.Automation.ValuePattern>、<xref:System.Windows.Automation.ValuePattern.SetValue%2A>方法用來插入文字控制項是使用者定義的字串。 否則，<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>使用方法。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>另請參閱  
 [TextPattern 插入文字範例](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
