---
title: "如何：將自訂資料加入至筆墨資料 | Microsoft Docs"
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
  - "筆墨資料, 加入自訂資料"
  - "InkCanvas, 顯示"
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：將自訂資料加入至筆墨資料
您可以將自訂資料新增至將儲存成為筆墨序列化格式 \(ISF\) 的筆墨。  您可以將自訂資料儲存至 <xref:System.Windows.Ink.DrawingAttributes>、<xref:System.Windows.Ink.StrokeCollection> 或 <xref:System.Windows.Ink.Stroke>。  將自訂資料儲存在三個物件上，可以讓您決定儲存資料的最佳位置。  這三種類別都使用類似的方法以儲存和存取自訂資料。  
  
 只有下面的型別可以儲存成自訂資料：  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>\[\]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>\[\]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>\[\]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>\[\]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>\[\]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>\[\]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>\[\]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>\[\]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>\[\]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>\[\]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>\[\]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>\[\]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>\[\]  
  
## 範例  
 下列範例說明如何從 <xref:System.Windows.Ink.StrokeCollection> 新增和擷取自訂資料。  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 下列範例會建立一個應用程式，會顯示一個 <xref:System.Windows.Controls.InkCanvas> 和兩個按鈕。  按鈕 `switchAuthor` 允許兩位不同作者使用兩支畫筆。  按鈕 `changePenColors` 會根據作者的設定，變更 <xref:System.Windows.Controls.InkCanvas> 上每一筆劃的色彩。  應用程式會定義兩個 <xref:System.Windows.Ink.DrawingAttributes> 物件，並各自新增一個自訂屬性，以標示哪一個 <xref:System.Windows.Ink.Stroke> 是由哪一位作者所寫的。  當使用者按一下 `changePenColors`，應用程式會根據自訂屬性的值變更筆劃的外觀。  
  
 [!code-xml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]