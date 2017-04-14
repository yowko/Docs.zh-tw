---
title: "如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 凍結"
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 資料行凍結"
  - "Windows Form, 資料行"
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行
當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集。  例如，在顯示包含許多資料行的客戶資訊資料表時，如果能在其他資料行在可見區域外捲動時，仍一直顯示客戶的名稱，將會非常有用。  
  
 若要達到這個行為，您可以凍結控制項中的資料行。  在凍結資料行時，也會凍結在該資料行左邊的所有資料行 \(或者，在由右往左的語言指令碼中，則會凍結右邊的資料行\)。  凍結的資料行會留在原處，而其他資料行則可以捲動。  如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。  使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具凍結資料行  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  在 \[**資料行屬性**\] 方格中，將 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> 屬性設定為 `true`。  
  
    > [!NOTE]
    >  您也可以選取 \[**加入資料行**\] 對話方塊中的 \[**凍結**\] 方塊，藉此在加入資料行時加以凍結。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中啟用資料行重新調整順序](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)   
 [How to: Display Right\-to\-Left Text in Windows Forms for Globalization](http://msdn.microsoft.com/zh-tw/f0663385-2354-4c65-8676-706422283b14)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)