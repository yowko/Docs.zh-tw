---
title: "如何：針對自動配置使用格線 | Microsoft Docs"
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
  - "自動配置, 方格使用"
  - "方格, 自動配置"
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：針對自動配置使用格線
本範例說明如何使用自動配置模式下的格線來建立可當地語系化的應用程式。  
  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的當地語系化是一項費時的處理程序。  除了翻譯文字以外，當地語系化人員通常還需要重新調整項目的大小和位置。  在過去，每當 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 需要顯示新的語言就必須進行調整。  現在，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的功能可以減少您需要對所設計項目進行的調整工作。  這種使應用程式的大小和位置更容易調整的撰寫方法稱為 `auto layout`。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會示範使用格線調整部分按鈕和文字的位置。  請注意，儲存格的高度和寬度都設為 `Auto`，因此包含影像按鈕的儲存格會隨影像調整大小。  因為 <xref:System.Windows.Controls.Grid> 項目可以隨其內容調整大小，所以以自動配置方法設計可以當地語系化的應用程式時相當有用。  
  
## 範例  
 下列範例顯示如何使用格線。  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
Grid  
  
## 請參閱  
 [使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [使用自動配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)