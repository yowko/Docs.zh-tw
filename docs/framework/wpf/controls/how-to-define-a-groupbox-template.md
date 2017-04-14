---
title: "如何：定義 GroupBox 範本 | Microsoft Docs"
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
  - "控制項, GroupBox"
  - "GroupBox 控制項, 建立範本"
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：定義 GroupBox 範本
這個範例說明如何建立 <xref:System.Windows.Controls.GroupBox> 控制項的範本。  
  
## 範例  
 下列範例使用版面配置的 <xref:System.Windows.Controls.Grid> 控制項來定義 <xref:System.Windows.Controls.GroupBox> 控制項範本。  本範例使用 <xref:System.Windows.Controls.BorderGapMaskConverter> 定義 <xref:System.Windows.Controls.GroupBox> 的框線，因此，框線不會混淆 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> 內容。  
  
 [!code-xml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GroupBox>   
 [GroupBox How\-to Topics](http://msdn.microsoft.com/zh-tw/7692e155-a4c6-428c-b7e0-64b3740daca7)