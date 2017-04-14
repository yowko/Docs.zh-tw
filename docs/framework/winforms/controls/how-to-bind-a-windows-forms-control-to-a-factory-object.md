---
title: "如何：將 Windows Form 控制項繫結至 Factory 物件 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 繫結至 Factory 物件"
  - "BindingSource 元件 [Windows Form], 範例"
  - "控制項 [Windows Form], 繫結"
  - "Factory 物件, 繫結至"
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將 Windows Form 控制項繫結至 Factory 物件
當您在建立與資料互動的控制項時，有時會發現需要將控制項繫結至會產生其他物件的物件或方法。  這類物件或方法就叫做 Factory。  比方說，您的資料來源可能是從方法呼叫傳回的值，而不是記憶體或類型中的物件。  只要來源傳回集合，您就可以將控制項繫結至這種資料來源。  
  
 使用 <xref:System.Windows.Forms.BindingSource> 控制項可讓您輕鬆將控制項繫結至 Factory 物件。  
  
## 範例  
 下列範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 控制項，將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 Factory 方法。  Factory 方法名為 `GetOrdersByCustomerId`，它會傳回 Northwind 資料庫中指定客戶的所有訂單。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)