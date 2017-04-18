---
title: "如何：擷取與 Windows Form 中檔案相關的圖示 | Microsoft Docs"
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
  - "在 ListView 控制項中顯示檔案名稱及其檔案類型圖示 [Windows Form]"
  - "擷取與檔案類型相關聯的圖示 [Windows Form]"
  - "副檔名圖示 [Windows Form], 在 ListView 中顯示"
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：擷取與 Windows Form 中檔案相關的圖示
許多檔案都有可提供相關聯檔案類型之視覺表示的內嵌圖示。  例如，Microsoft Word 文件就包含可將其識別為 Word 文件的圖示。  在清單控制項或表格控制項中顯示檔案時，您必須在每個檔案名稱的旁邊顯示代表檔案類型的圖示。  這時您只要使用 <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> 方法，便可輕易完成這個動作。  
  
## 範例  
 下列程式碼範例會示範如何擷取與檔案關聯的圖示，並在 <xref:System.Windows.Forms.ListView> 控制項中顯示檔案名稱及其關聯的圖示。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 若要編譯此範例：  
  
-   將先前的程式碼貼入 Windows Form，並從表單的建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `ExtractAssociatedIconExample` 方法。  
  
     您將需要確定您的表單有匯入 <xref:System.IO> 命名空間 \(Namespace\)。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)