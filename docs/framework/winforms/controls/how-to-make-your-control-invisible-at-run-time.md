---
title: "如何：在執行階段期間隱藏控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 在執行階段變成不可見"
  - "自訂控制項 [Windows Form], 不可見的"
  - "不可見的控制項"
  - "執行階段, 讓控制項變成不可見"
  - "使用者控制項 [Windows Form], 不可見的"
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在執行階段期間隱藏控制項
有時候，您可能要建立會在執行階段隱藏的使用者控制項。  例如，只有在鬧鈴響的時候才出現的鬧鐘控制項。  您可藉由設定 <xref:System.Windows.Forms.Control.Visible%2A> 屬性來輕鬆達成這個目的。  如果 <xref:System.Windows.Forms.Control.Visible%2A> 屬性為 `true`，控制項會照常出現。  如果為 `false`，則會隱藏控制項。  雖然控制項在隱藏時還是可執行其中的程式碼，但您無法透過使用者介面與控制項互動。  如果您要建立還是能回應使用者輸入 \(例如按一下滑鼠\) 的不可見控制項，您應建立透明的控制項。  如需詳細資訊，請參閱[為您的控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)。  
  
### 若要在執行階段期間隱藏控制項  
  
1.  將 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `false`。  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Visible%2A>   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [如何：為控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)