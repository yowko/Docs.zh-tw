---
title: "如何：擴展 TableLayoutPanel 控制項中的資料列和資料行 | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "儲存格, 合併"
  - "資料行 [Windows Form], 擴展"
  - "合併儲存格"
  - "資料列 [Windows Form], 擴展"
  - "TableLayoutPanel 控制項 [Windows Form], 擴展資料列和資料行"
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：擴展 TableLayoutPanel 控制項中的資料列和資料行
<xref:System.Windows.Forms.TableLayoutPanel> 控制項中的控制項可以擴展相鄰的資料列和資料行。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要擴展資料行和資料列  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  從 \[**工具箱**\] 拖曳 <xref:System.Windows.Forms.Button> 控制項至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左上方儲存格。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項的 \[**ColumnSpan**\] 屬性設定為 2。  請注意 <xref:System.Windows.Forms.Button> 控制項會擴展第一個和第二個資料行。  
  
4.  將 <xref:System.Windows.Forms.Button> 控制項的 \[**RowSpan**\] 屬性設定為 2。  請注意 <xref:System.Windows.Forms.Button> 控制項會擴展第一個和第二個資料列。  
  
5.  將 <xref:System.Windows.Forms.Button> 控制項的 \[**ColumnSpan**\] 屬性設定為 1。  請注意 <xref:System.Windows.Forms.Button> 控制項會移入第一個資料行，並擴展第一個和第二個資料列。  
  
## 請參閱  
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)