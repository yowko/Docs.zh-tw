---
title: "如何：編輯 TableLayoutPanel 控制項中的資料行和資料列 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.StyleCollectionEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料行 [Windows Form], 編輯"
  - "資料列 [Windows Form], 編輯"
  - "TableLayoutPanel 控制項 [Windows Form], 編輯"
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：編輯 TableLayoutPanel 控制項中的資料行和資料列
您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的集合編輯器 \(稱為 \[**資料行和資料列樣式**\] 對話方塊\) 來編輯控制項的資料列和資料行。  
  
> [!NOTE]
>  如果您想要控制項能夠擴展多個資料列或資料行，請設定控制項上的 `RowSpan` 和 `ColumnSpan` 屬性。  如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  如果希望對齊儲存格內的控制項，或想要控制項在儲存格中自動縮放，請使用控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。  如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要編輯資料列和資料行  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  按一下 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料列和資料行**\] 以開啟 \[**資料行和資料列樣式**\] 對話方塊。  您也能以滑鼠右鍵按一下 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，然後從捷徑功能表選取 \[**編輯資料列和資料行**\]。  
  
3.  若要新增或移除資料行，請從 \[**成員型別**\] 下拉式清單方塊中選取 \[**資料行**\]。  
  
4.  若要新增或移除資料列，請從 \[**成員型別**\] 下拉式清單方塊中選取 \[**資料列**\]。  
  
5.  按一下 \[**加入**\] 按鈕，將資料列或資料行加入至 \[**成員**\] 清單的結尾。  
  
6.  按一下 \[**插入**\] 按鈕，將資料列或資料行加入清單中目前選取的項目之前。  
  
7.  如果您加入資料列或資料行，請選取新資料列或資料行的 \[**大小類型**\]。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.SizeType>。  
  
8.  若要移除資料列或資料行，請按一下 \[**移除**\] 按鈕以刪除 \[**成員**\] 清單中目前選取的項目。  
  
## 請參閱  
 <xref:System.Windows.Forms.SizeType>   
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)