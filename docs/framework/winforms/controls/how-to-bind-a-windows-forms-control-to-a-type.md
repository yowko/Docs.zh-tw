---
title: "如何：將 Windows Form 控制項繫結至類型 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 繫結至類型"
  - "控制項 [Windows Form], 繫結至類型"
  - "類型 [Windows Form], 將控制項繫結至"
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：將 Windows Form 控制項繫結至類型
當您在建立與資料互動的控制項時，有時會發現有必要將控制項繫結至類型，而非物件。  特別是在設計階段會發生這種情況，此時資料可能無法使用，但是資料繫結控制項仍然需要顯示類型公用介面中的資訊。  例如，您可能會繫結 <xref:System.Windows.Forms.DataGridView> 控制項至 Web 服務所公開的物件，並想讓 <xref:System.Windows.Forms.DataGridView> 控制項將設計階段的資料行標記為自訂類型的成員名稱。  
  
 您可以輕鬆地繫結控制項至具有 <xref:System.Windows.Forms.BindingSource> 元件的類型。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至自訂類型。  當您執行範例時，您會注意到在控制項填入資料之前，<xref:System.Windows.Forms.DataGridView> 標記會反映 `Customer` 物件屬性的資料行。  此範例包含 \[Add Customer\] 按鈕，以將資料加入至 <xref:System.Windows.Forms.DataGridView> 控制項。  當您按一下按鈕，新 `Customer` 物件會加入至 <xref:System.Windows.Forms.BindingSource>。  在實際案例中，可能會透過呼叫 Web 服務或其他資料來源取得資料。  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   本系統以及 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)