---
title: "如何：將控制項加入至索引標籤頁 | Microsoft Docs"
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
  - "索引標籤控制項, 定位順序"
  - "索引標籤頁, 加入控制項"
  - "TabPage 控制項"
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：將控制項加入至索引標籤頁
您可以使用 Windows Form 的 <xref:System.Windows.Forms.TabControl>，以有組織的方式顯示其他控制項。  下列程序示範如何將按鈕加入至第一個索引標籤。  如需將圖示加入至索引標籤頁之標籤部分的詳細資訊，請參閱 [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)。  
  
### 若要以程式設計方式加入控制項  
  
1.  使用由 <xref:System.Windows.Forms.TabPage> 的 <xref:System.Windows.Forms.Control.Controls%2A> 屬性所傳回的集合之 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> 方法。  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## 請參閱  
 [TabControl 控制項](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)   
 [如何：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [如何：使用 Windows Form TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)