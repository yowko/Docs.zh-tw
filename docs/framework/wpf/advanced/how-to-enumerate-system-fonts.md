---
title: "如何：列舉系統字型 | Microsoft Docs"
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
  - "列舉, 系統字型"
  - "字型, 列舉"
  - "系統字型, 列舉"
  - "印刷樣式, 列舉系統字型"
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：列舉系統字型
## 範例  
 下列範例顯示如何列舉系統字型集合中的字型。  <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> 內每個 <xref:System.Windows.Media.FontFamily> 的字型系列名稱都會加入成為下拉式方塊的項目。  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 如果同一字型系列，在相同目錄中有多個版本，則 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 字型列舉型別會傳回最新的字型版本。  如果版本資訊並未提供解決方式，則會傳回具有最近時間戳記的字型。  如果時間戳記資訊相同，則會按照字母順序傳回第一個字型檔案。