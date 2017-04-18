---
title: "如何：使用設計工具載入圖片 (Windows Form) | Microsoft Docs"
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
  - "表單, 顯示影像"
  - "影像 [Windows Form], 在 Windows Form 上顯示"
  - "圖片格式"
  - "PictureBox 控制項 [Windows Form], 加入圖片"
  - "圖片, 顯示"
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用設計工具載入圖片 (Windows Form)
使用 Windows Form <xref:System.Windows.Forms.PictureBox> 控制項，您可以將 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性設定為有效的圖片，藉此在設計階段於表單上載入與顯示圖片。  下表顯示可接受的檔案類型。  
  
|型別|副檔名|  
|--------|---------|  
|點陣圖|.bmp|  
|圖示|.ico|  
|GIF|.gif|  
|中繼檔 \(Metafile\)|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段顯示圖片  
  
1.  將 <xref:System.Windows.Forms.PictureBox> 控制項拖曳至表單上。  
  
2.  在 \[屬性\] 視窗上選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性，然後按一下省略按鈕以顯示 \[**開啟**\] 對話方塊。  
  
3.  如果正在搜尋特定的檔案類型 \(例如，.gif 檔\)，請在 \[**檔案類型**\] 方塊中選取它。  
  
4.  選取要顯示的檔案。  
  
### 若要在設計階段清除圖片  
  
1.  在 \[**屬性**\] 視窗中，選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性，並以滑鼠右鍵按一下影像物件名稱左邊的縮圖影像。  選擇 \[**重設**\]。  
  
## 請參閱  
 <xref:System.Windows.Forms.PictureBox>   
 [PictureBox 控制項概觀](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [如何：於執行階段修改圖片的大小或位置](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [如何：在執行階段設定圖案](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox 控制項](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)