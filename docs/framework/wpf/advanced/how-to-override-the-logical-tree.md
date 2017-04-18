---
title: "如何：覆寫邏輯樹狀結構 | Microsoft Docs"
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
  - "邏輯樹狀結構, 覆寫"
  - "覆寫邏輯樹狀結構"
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：覆寫邏輯樹狀結構
雖然這在大多數情況下並不需要，不過資深控制項作者可選擇覆寫[邏輯樹狀結構](GTMT)。  
  
## 範例  
 本範例說明如何使用子類別 <xref:System.Windows.Controls.StackPanel> 來覆寫邏輯樹狀結構，在此例中，就是強制面板只能也只會呈現一個子項目的行為。  這不一定是實際所需的行為，而只是為了示範如何覆寫項目的一般邏輯樹狀結構。  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 如需邏輯樹狀結構的詳細資訊，請參閱[WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。