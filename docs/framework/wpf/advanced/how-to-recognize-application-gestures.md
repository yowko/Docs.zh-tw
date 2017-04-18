---
title: "如何：辨認應用程式筆勢 | Microsoft Docs"
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
  - "應用程式筆勢, 辨識"
  - "筆勢, 辨識"
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：辨認應用程式筆勢
下列範例說明當使用者在 <xref:System.Windows.Controls.InkCanvas> 上執行 <xref:System.Windows.Ink.ApplicationGesture> 動作時，如何清除筆墨。  本範例會假設 <xref:System.Windows.Controls.InkCanvas> \(名稱為 `inkCanvas1`\) 已在 XAML 檔案中宣告。  
  
## 範例  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Ink.ApplicationGesture>   
 <xref:System.Windows.Controls.InkCanvas>   
 <xref:System.Windows.Controls.InkCanvas.Gesture>