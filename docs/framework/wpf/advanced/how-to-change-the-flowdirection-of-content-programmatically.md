---
title: "如何：以程式設計方式變更內容的 FlowDirection | Microsoft Docs"
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
  - "文件, 以程式設計方式變更 FlowDirection 屬性"
  - "FlowDirection 屬性, 以程式設計方式變更"
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：以程式設計方式變更內容的 FlowDirection
這個範例顯示如何以程式設計方式變更 <xref:System.Windows.Controls.FlowDocumentReader> 的 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性。  
  
## 範例  
 會建立兩個 <xref:System.Windows.Controls.Button> 項目，而每個項目都代表 <xref:System.Windows.FlowDirection> 的其中一個可能值。  按一下按鈕時，相關聯的屬性值會套用至 <xref:System.Windows.Controls.FlowDocumentReader> \(名為 `tf1`\) 的內容。  而屬性值也會寫入至 <xref:System.Windows.Controls.TextBlock> \(名為 `txt1`\)。  
  
 [!code-xml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## 範例  
 與上面定義之按鈕按一下動作相關聯的事件，是在 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 程式碼後置 \(Code\-Behind\) 檔案中進行處理。  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]