---
title: "如何：使用 BindingSource 元件跨表單共用繫結資料 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 範例"
  - "BindingSource, 配合多個表單使用"
  - "資料繫結, 跨表單共用資料"
  - "範例 [Windows Form], BindingSource 元件"
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用 BindingSource 元件跨表單共用繫結資料
您可以使用 <xref:System.Windows.Forms.BindingSource> 元件輕鬆地跨表單共用資料。  例如，您可能想要顯示一個唯讀表單，該表單會摘要資料來源資料，並顯示另一個可編輯的表單，其中包含在資料來源中目前所選取項目的詳細資訊。  這個範例將示範此案例。  
  
## 範例  
 下列程式碼範例示範如何跨表單共用 <xref:System.Windows.Forms.BindingSource> 及其繫結的資料。  在此範例中，會傳遞共用的 <xref:System.Windows.Forms.BindingSource> 至子表單的建構函式。  子表單可讓使用者在主表單中編輯目前所選取項目的資料。  
  
> [!NOTE]
>  在此範例中，會處理 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以確保這兩個表單維持同步處理。  如須為何進行此動作的詳細資訊，請參閱[如何：確保繫結至相同資料來源的多個控制項都能保持同步](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Windows.Forms、System.Drawing、System.Data 和 System.Xml 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [如何：處理資料繫結時所發生的錯誤和例外狀況](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)