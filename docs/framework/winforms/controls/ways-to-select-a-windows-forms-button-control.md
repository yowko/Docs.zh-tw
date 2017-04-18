---
title: "選取 Windows Form Button 控制項的方法 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], 選取"
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 選取 Windows Form Button 控制項的方法
您可以使用下列方法來選取 Windows Form 按鈕：  
  
-   用滑鼠按一下按鈕。  
  
-   在程式碼中叫用 \(Invoke\) 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
-   將焦點 \(Focus\) 移至按鈕，方法是按下 TAB 鍵，然後按下空格鍵或 ENTER 來選擇按鈕。  
  
-   按下按鈕的便捷鍵 \(ALT \+ 加上底線的字元\)。  如需便捷鍵的詳細資訊，請參閱 [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。  
  
-   如果按鈕是表單的「接受」按鈕，則除非另一個控制項是其他按鈕、多行文字方塊或會截獲 ENTER 鍵的自訂控制項，否則按下 ENTER 便會選擇該按鈕，即使另一個控制項擁有焦點也是如此。  
  
-   如果按鈕是表單的「取消」按鈕，則即使另一個控制項擁有焦點，按下 ESC 鍵也會選擇該按鈕。  
  
-   以程式設計方式呼叫 <xref:System.Windows.Forms.Button.PerformClick%2A> 方法來選取按鈕。  
  
## 請參閱  
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)