---
title: "如何：存取物件繫結至 Windows Form DataGridView 資料列 | Microsoft Docs"
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
  - "資料格, 存取繫結物件"
  - "DataGridView 控制項 [Windows Form], 存取繫結到資料列的物件"
  - "物件繫結, 存取繫結物件"
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：存取物件繫結至 Windows Form DataGridView 資料列
有時候顯示儲存在商務物件集合中之資料表的資訊會很有用。  當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項至這類集合，則每個公用屬性會顯示在自己的資料行中​​，除非屬性已標示為不可由 <xref:System.ComponentModel.BrowsableAttribute> 瀏覽。  例如，`Customer` 物件的集合可能有例如 \[名稱\] 和 \[位址\] 的資料行。  
  
 如果這些物件包含其他資訊和您想要存取的程式碼，您可透過資料列物件取得。  在下列程式碼範例中，使用者可以選取多個資料列，然後按一下按鈕將發票傳送至每個對應的客戶。  
  
### 若要存取資料列繫結物件  
  
-   請使用 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=fullName> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## 範例  
 完整的程式碼範例包含簡單的 `Customer` 實作以及繫結 <xref:System.Windows.Forms.DataGridView> 至包含幾個 `Customer` 物件的 <xref:System.Collections.ArrayList>。  <xref:System.Windows.Forms.Button?displayProperty=fullName> 的 <xref:System.Windows.Forms.Control.Click> 事件處理常式必須透過資料列存取 `Customer` 物件，因為客戶集合並不能從 <xref:System.Windows.Forms.Form.Load?displayProperty=fullName> 事件處理常式的外部存取。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewRow>   
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [如何：將物件繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)