---
title: "如何：取得頁面函式的傳回值 | Microsoft Docs"
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
  - "函式, 取得傳回值"
  - "取得, 頁面函式的傳回值"
  - "頁面函式, 取得傳回值"
  - "頁面函式的傳回值"
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：取得頁面函式的傳回值
本範例示範如何取得頁面函式傳回的結果。  
  
## 範例  
 若要取得頁面函式傳回的結果，您必須處理所呼叫之頁面函式的 <xref:System.Windows.Navigation.PageFunction%601.Return>。  
  
 [!code-xml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## 請參閱  
 <xref:System.Windows.Navigation.PageFunction%601>