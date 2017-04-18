---
title: "如何：呈現視覺化樣式項目 | Microsoft Docs"
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
  - "專業外觀, 套用到 Windows Form 應用程式的項目"
  - "視覺化樣式, 呈現 Windows Form 控制項"
  - "視覺化佈景主題, 套用到 Windows Form 應用程式的項目"
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：呈現視覺化樣式項目
<xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間會公開 \(Expose\) <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 物件，此物件表示由視覺樣式所支援的 Windows 使用者介面 \(UI\) 項目。  這個主題示範如何使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 類別呈現表示 \[開始\] 功能表的 \[**登出**\] 和 \[**關閉**\] 按鈕的 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>。  
  
### 若要呈現視覺樣式項目  
  
1.  建立 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 並將它設定為要繪製的項目。  請注意使用 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=fullName> 屬性和 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=fullName> 方法；如果停用了視覺樣式或未定義項目，<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> 建構函式便會擲出例外狀況。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  請呼叫 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> 方法以呈現 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 目前所表示的項目。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   衍生自 <xref:System.Windows.Forms.Control> 類別的自訂控制項。  
  
-   裝載自訂控制項的 <xref:System.Windows.Forms.Form>。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間的參考。  
  
## 請參閱  
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)