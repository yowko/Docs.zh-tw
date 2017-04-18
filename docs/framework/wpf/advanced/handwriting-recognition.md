---
title: "手寫辨識 | Microsoft Docs"
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
  - "手寫辨識"
  - "手寫辨識"
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 手寫辨識
本章節討論辨識 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 平台數位筆墨相關的基本原理。  
  
## 辨識方案  
 下列範例顯示如何使用 <xref:System.Windows.Ink.InkAnalyzer> 辨識筆墨。  
  
> [!NOTE]
>  這個範例需要在系統上安裝手寫辨識器。  
  
 在 Visual Studio 2005 中建立名為 InkRecognition 的新 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  將 Window1.xaml 檔案的內容取代成下列 XAML 程式碼。  這段程式碼會呈現應用程式的使用者介面。  
  
 [!code-xml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 加入 WPF Ink Analysis 組件 IAWinFX.dll、IACore.dll 和 IALoader.dll 的參考，這些組件可以在 \\Program Files\\Reference Assemblies\\Microsoft\\Tablet PC\\v1.7 中找到。  將程式碼後置檔案的內容取代成下列程式碼。  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Ink.InkAnalyzer>   
 <xref:System.Windows.Ink.AnalysisStatus>   
 <xref:System.Windows.Controls.InkCanvas>