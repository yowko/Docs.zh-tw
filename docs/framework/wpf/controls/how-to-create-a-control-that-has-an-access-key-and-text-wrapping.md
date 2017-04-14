---
title: "如何：建立有便捷鍵和自動換行的控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "便捷鍵, 控制項"
  - "控制項, 便捷鍵"
  - "控制項, 文字換行"
  - "索引鍵, 控制項"
  - "文字換行"
  - "文字換行"
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：建立有便捷鍵和自動換行的控制項
本範例顯示如何建立具有[便捷鍵](GTMT) \(Access Key\) 並支援自動換行的控制項。  這個範例使用 <xref:System.Windows.Controls.Label> 控制項來說明這些概念。  
  
## 範例  
 **將自動換行加入到標籤**  
  
 <xref:System.Windows.Controls.Label> 控制項不支援自動換行。  如果您需要能夠自動換行的標籤，可以在標籤內巢狀嵌入另一個支援自動換行的項目。  下列範例顯示如何使用 <xref:System.Windows.Controls.TextBlock>，讓標籤能夠自動換行多行文字。  
  
 [!code-xml[Label#5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#5)]
 [!code-xml[Label#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#5)]  
  
 **將便捷鍵和自動換行加入到標籤**  
  
 如果您需要有便捷鍵 \(助憶鍵 \(Mnemonic\)\) 的 <xref:System.Windows.Controls.Label>，請在 <xref:System.Windows.Controls.Label> 內使用 <xref:System.Windows.Controls.AccessText> 項目。  
  
 像是 <xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.RadioButton>、<xref:System.Windows.Controls.CheckBox>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.TabItem>、<xref:System.Windows.Controls.Expander> 和 <xref:System.Windows.Controls.GroupBox> 之類的控制項都有預設控制項樣板。  這些樣板包含 <xref:System.Windows.Controls.ContentPresenter>。  您可以在 <xref:System.Windows.Controls.ContentPresenter> 上設定的其中一個屬性就是 <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>\="true"，這可用來指定控制項的便捷鍵。  
  
 下列範例顯示如何建立具有便捷鍵並支援自動換行的 <xref:System.Windows.Controls.Label>。  為啟用自動換行，此範例設定了 <xref:System.Windows.Controls.AccessText.TextWrapping%2A> 屬性並使用底線字元指定便捷鍵   \(緊接在底線字元後面的字元就是便捷鍵\)。  
  
 [!code-xml[Label#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#4)]
 [!code-xml[Label#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#4)]  
  
## 請參閱  
 [How to: Set the Target Property of a Label](http://msdn.microsoft.com/zh-tw/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)