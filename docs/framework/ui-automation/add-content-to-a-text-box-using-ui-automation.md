---
title: "Add Content to a Text Box Using UI Automation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adding content to text boxes"
  - "text boxes, adding content"
  - "UI Automation, adding content to text boxes"
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: 13
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 13
---
# Add Content to a Text Box Using UI Automation
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。  如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746) \(英文\)。  
  
 本主題中的程式碼範例會示範如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]，將文字插入單行的文字方塊。  其他方法供多行和 Rich Text 控制項之用，其中 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不適用。  為了進行比較，本範例也會說明如何使用 Win32 方法完成相同的結果。  
  
## 範例  
 下列範例會在目標應用程式中逐步執行文字控制項的序列。  每個文字控制項都會經過測試，以確認是否可使用 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 方法取得 <xref:System.Windows.Automation.ValuePattern> 物件。  如果文字控制項不支援 <xref:System.Windows.Automation.ValuePattern>，即可使用 <xref:System.Windows.Automation.ValuePattern.SetValue%2A> 方法，將使用者定義字串插入文字控制項中。  否則，會使用 <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=fullName> 方法。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## 請參閱  
 [TextPattern Insert Text Sample](http://msdn.microsoft.com/zh-tw/67353f93-7ee2-42f2-ab76-5c078cf6ca16)