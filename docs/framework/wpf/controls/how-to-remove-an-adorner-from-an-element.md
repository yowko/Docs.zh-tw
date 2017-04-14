---
title: "如何：從項目移除裝飾項 | Microsoft Docs"
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
  - "Adorner, 移除"
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：從項目移除裝飾項
本範例示範如何以程式設計的方式，從指定的 <xref:System.Windows.UIElement> 移除特定裝飾項。  
  
## 範例  
 這個詳細的程式碼範例會移除 <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> 傳回之裝飾項陣列中的第一個裝飾項。  此範例擷取的裝飾項剛好位於名稱為 *myTextBox* 的 <xref:System.Windows.UIElement> 上。  如果呼叫 <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> 時指定的項目沒有任何裝飾項，則會傳回 `null`。  這個程式碼會明確檢查 null 陣列，因此最適合 null 陣列應該相當常見的應用程式。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## 範例  
 這個濃縮版的程式碼範例在功能上相當於前面顯示的詳細範例。  這個程式碼不會明確檢查 null 陣列，因此可能會引發 <xref:System.NullReferenceException> 例外狀況。  這個程式碼最適合 null 陣列較為少見的應用程式。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## 請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)