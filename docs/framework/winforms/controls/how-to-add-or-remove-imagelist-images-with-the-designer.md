---
title: "如何：使用設計工具加入或移除 ImageList 影像 | Microsoft Docs"
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
  - "ImageList 元件 [Windows Form], 加入影像"
  - "ImageList 元件 [Windows Form], 移除影像"
  - "影像 [Windows Form], 加入至 ImageList 元件"
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用設計工具加入或移除 ImageList 影像
您可以使用數種不同的方式在 <xref:System.Windows.Forms.ImageList> 元件中加入影像。  您可以利用與 <xref:System.Windows.Forms.ImageList> 關聯的智慧標籤很快地加入影像，或者，如果您在 <xref:System.Windows.Forms.ImageList> 上設定了數個其他屬性，您可能會發現用 \[屬性\] 視窗會來得更方便。  您也可以使用程式碼來加入影像。  如需如何使用程式碼加入影像的詳細資訊，請參閱 [如何：使用 Windows Form ImageList 元件加入或移除影像](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  通常您會在 <xref:System.Windows.Forms.ImageList> 元件與控制項產生關聯之前，先在元件中填入影像，但不一定要這麼做。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用屬性視窗加入或移除影像  
  
1.  選取 <xref:System.Windows.Forms.ImageList> 元件，或將一個元件加入至表單。  
  
2.  在 \[屬性\] 視窗中，按一下 <xref:System.Windows.Forms.ImageList.Images%2A> 屬性旁邊的省略符號按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  
  
3.  在 \[**影像集合編輯器**\] 中，按一下 \[**加入**\] 或 \[**移除**\] 以將影像加入至清單，或從清單中移除。  
  
### 若要使用智慧標籤加入或移除影像  
  
1.  選取 <xref:System.Windows.Forms.ImageList> 元件，或將一個元件加入至表單。  
  
2.  按一下智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)  
  
3.  在 \[**ImageList 工作**\] 對話方塊中，選取 \[**選擇影像**\]。  
  
4.  在 \[**影像集合編輯器**\] 中，按一下 \[**加入**\] 或 \[**移除**\] 以將影像加入至清單，或從清單中移除。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)   
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)