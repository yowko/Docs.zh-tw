---
title: "如何：調整 Windows Form Label 控制項大小以適合其內容 | Microsoft Docs"
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
  - "標題, 調整大小"
  - "Label 控制項 [Windows Form], 調整大小以符合內容"
  - "標籤, 調整大小以符合內容"
  - "大小, 控制項"
  - "調整控制項大小"
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：調整 Windows Form Label 控制項大小以適合其內容
Windows Form <xref:System.Windows.Forms.Label> 控制項可為單行或多行，而且可為固定大小，或自動調整大小以容納其標題。  <xref:System.Windows.Forms.Label.AutoSize%2A> 屬性可助您調整控制項大小以容納更大或更小的標題，如果標題會在執行階段變更，這便會特別有用。  
  
### 若要動態調整 label 控制項大小以適合其內容  
  
1.  將 <xref:System.Windows.Forms.Label.AutoSize%2A> 屬性設定為 `true`。  
  
 若 <xref:System.Windows.Forms.Label.AutoSize%2A> 設為 `false`，則在 <xref:System.Windows.Forms.Label.Text%2A> 屬性中指定的字在可能的情況下會換行至下一行，但控制項並不會放大。  
  
## 請參閱  
 [如何：使用 Windows Form Label 控制項建立便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)   
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label 控制項](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)