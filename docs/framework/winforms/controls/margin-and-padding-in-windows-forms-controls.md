---
title: "Windows Form 控制項的邊界和邊框距離 | Microsoft Docs"
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
  - "版面配置 [Windows Form], 邊界和邊框距離"
  - "Margin 屬性 [Windows Form]"
  - "Padding 屬性 [Windows Form]"
  - "Windows Form, 配置"
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Windows Form 控制項的邊界和邊框距離
對許多應用程式而言，控制項在表單上的精確位置是高優先順序。  <xref:System.Windows.Forms?displayProperty=fullName> 命名空間提供您許多版面配置功能來完成這項作業。  最重要的兩項是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 \(例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值\) 與控制項的邊框保持指定的距離。  
  
 下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
 ![Windows Form 控制項的邊框距離和邊界](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS\_WinFormPadMargin")  
  
 Visual Studio 中有針對此功能提供的設計階段支援。  另請參閱[逐步解說：使用邊框距離、邊界和 AutoSize 屬性來配置 Windows Form 控制項](http://msdn.microsoft.com/library/3z3f9e8b%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.Control.Margin%2A>   
 <xref:System.Windows.Forms.Control.Padding%2A>   
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>