---
title: "如何：實作自訂配置引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "FlowLayoutPanel 控制項 [Windows Form], 配置引擎"
  - "配置引擎, 自訂"
  - "配置引擎, 實作"
  - "LayoutEngine 類別"
  - "TableLayoutPanel 控制項 [Windows Form], 配置引擎"
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：實作自訂配置引擎
下列程式碼範例示範如何建立執行簡單流程配置的自訂配置引擎。  它會實作名為 `DemoFlowPanel` 的面板控制項，這會覆寫 <xref:System.Windows.Forms.Control.LayoutEngine%2A> 屬性以提供 `DemoFlowLayout` 類別的執行個體。  
  
## 範例  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Forms.Layout.LayoutEngine>   
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=fullName>