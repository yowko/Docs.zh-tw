---
title: "如何：使用 Windows Form BindingNavigator 控制項在資料集中移動 | Microsoft Docs"
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
  - "BindingNavigator 控制項 [Windows Form], 在資料集中移動"
  - "資料集 [Windows Form], 移動"
  - "範例 [Windows Form], BindingNavigator 控制項"
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form BindingNavigator 控制項在資料集中移動
當您建立資料驅動應用程式時，通常需要向使用者顯示資料集合。  <xref:System.Windows.Forms.BindingNavigator> 控制項搭配 <xref:System.Windows.Forms.BindingSource> 元件提供方便且可擴充的方案，可在集合中移動並循序顯示項目。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingNavigator> 控制項在資料中移動。  這個集合會包含在使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Data.DataView> 中。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)