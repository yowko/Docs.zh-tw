---
title: "如何：列舉列印佇列的子集 | Microsoft Docs"
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
  - "列舉, 列印佇列的子集"
  - "列印佇列, 列舉子集"
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：列舉列印佇列的子集
資訊技術 \(IT\) 專業人員在管理全公司的印表機時經常面對的情況之一，是必須產生具有某些特性的印表機清單。  這項功能由 <xref:System.Printing.PrintServer> 物件與 <xref:System.Printing.EnumeratedPrintQueueTypes> 列舉型別的 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法所提供。  
  
## 範例  
 在下列範例中，程式碼首先會建立旗標陣列，以指定我們要列出的列印佇列特性。  在此範例中，我們將尋找已安裝在本機列印伺服器上並且共用的列印佇列。  <xref:System.Printing.EnumeratedPrintQueueTypes> 列舉型別可提供許多其他可能性。  
  
 程式碼接著會建立 <xref:System.Printing.LocalPrintServer> 物件，此為衍生自 <xref:System.Printing.PrintServer> 的類別。  本機列印伺服器為執行應用程式的電腦。  
  
 最後一個重要步驟是將陣列傳送至 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 您可以讓每個列印佇列中所執行的 `foreach` 迴圈 \(Loop\) 進行進一步的篩選，以擴充此範例。  例如，您可以讓迴圈呼叫每個列印佇列的 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法以篩選掉不支援雙面列印的印表機，並測試雙面列印存在時的傳回值。  
  
## 請參閱  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)