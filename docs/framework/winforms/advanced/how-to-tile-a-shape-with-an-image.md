---
title: "如何：使用影像並排顯示圖案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "點陣圖 [Windows Form], 用以填滿圖案"
  - "影像 [Windows Form], 用以填滿圖案"
  - "圖案, 與影像並排"
  - "紋理筆刷, 並排影像"
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用影像並排顯示圖案
就好像您可以將瓷磚並排來拼接地板，您也可以將矩形影像並排來填滿 \(並排顯示\) 圖案。  若要並排顯示圖案的內部，請使用材質筆刷。  當您建構 <xref:System.Drawing.TextureBrush> 物件時，傳遞至建構函式的引數之一為 <xref:System.Drawing.Image> 物件。  當您使用材質筆刷繪製圖案的內部時，便會使用這個影像的重複複本來填滿圖案。  
  
 <xref:System.Drawing.TextureBrush> 物件的換行模式屬性會決定影像在矩形格線中重複的方向。  您可以使格線中的所有拼接都朝相同的方向，也可以將影像從一個格線位置翻轉至另一個位置。  翻轉方向可為水平、垂直或兩者。  下列範例會說明使用不同翻轉類型的拼接。  
  
### 若要並排顯示影像  
  
-   這個範例使用下列的 75×75 影像來並排顯示 200×200 的矩形。  
  
 ![磚 1](../../../../docs/framework/winforms/advanced/media/tile1.png "tile1")  
  
-   下圖顯示的是如何使用影像拼接成矩形。  請注意，所有拼接的方向都相同，沒有進行任何翻轉。  
  
 ![磚 2](../../../../docs/framework/winforms/advanced/media/tile2.png "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### 若要在並排顯示時水平地翻轉影像  
  
-   這個範例使用相同的 75×75 影像來填滿 200×200 的矩形。  換行模式已設定為水平翻轉影像。  下圖顯示的是如何使用影像拼接成矩形。  請注意，當您從一個拼接移到同一列的下一個拼接時，即會水平翻轉影像。  
  
 ![磚 3](../../../../docs/framework/winforms/advanced/media/tile3.png "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### 若要在並排顯示時垂直地翻轉影像  
  
-   這個範例使用相同的 75×75 影像來填滿 200×200 的矩形。  換行模式已設定為垂直翻轉影像。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### 若要在並排顯示時水平和垂直地翻轉影像  
  
-   這個範例使用相同的 75×75 影像來並排顯示 200×200 的矩形。  換行模式已設定為同時水平和垂翻轉影像。  下圖顯示的是如何使用影像拼接成矩形。  請注意，當您從一個拼接移到同一列的下一個拼接時，即會水平翻轉影像；當您從一個拼接移到同一行的下一個拼接時，則會垂直翻轉影像。  
  
 ![磚 5](../../../../docs/framework/winforms/advanced/media/tile5.png "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## 請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)