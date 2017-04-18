---
title: "如何：使用自動配置建立按鈕 | Microsoft Docs"
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
  - "自動配置, 建立按鈕"
  - "Button 控制項, 使用自動配置建立"
  - "建立, 使用自動配置的按鈕"
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用自動配置建立按鈕
本範例說明如何使用自動配置方法來建立可當地語系化的應用程式。  
  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的當地語系化是一項費時的處理程序。  除了翻譯文字以外，當地語系化工程師通常還需要重新調整項目的大小和位置。  在過去，每當 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 需要顯示新的語言就必須進行調整。  現在，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的功能可以減少您需要對所設計項目進行的調整工作。  用以撰寫可更輕鬆調整大小和位置之應用程式的方法稱為 `automatic layout`。  
  
 下列兩個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會建立可具現化 \(Instantiate\) 按鈕的應用程式，其中一個按鈕為英文，另一個則為西班牙文。  請注意，除了文字以外，程式碼都一樣，按鈕會配合文字進行調整。  
  
## 範例  
 [!code-xml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![按鈕相同，但文字的語言不同](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
可自動調整大小的按鈕  
  
## 請參閱  
 [使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [針對自動配置使用格線](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)