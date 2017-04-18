---
title: "Label 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "Label"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "影像 [Windows Form], 在標籤中顯示"
  - "Label 控制項 [Windows Form], 關於 Label 控制項"
  - "標籤"
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Label 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Label> 控制項是用來顯示使用者無法編輯的文字或影像。  它們是用來識別表單的物件，例如，它可描述在按一下特定的控制項時將執行哪些動作，或顯示資訊以回應應用程式中的執行階段事件或處理序 \(Process\)。  例如，您可以使用標籤 \(Label\)，將描述性標題加入文字方塊、清單方塊、下拉式方塊等等。  您也可以撰寫程式碼以變更標籤顯示的文字，來回應執行階段的事件。  例如，如果應用程式需花數分鐘以處理變更，您可以顯示標籤中的處理狀態訊息。  
  
## 使用標籤控制項  
 因為 <xref:System.Windows.Forms.Label> 控制項無法接收焦點 \(Focus\)，所以它也可用來建立其他控制項的便捷鍵 \(Access Key\)。  便捷鍵可讓使用者選取其他控制項，只要藉由按下 ALT 鍵及便捷鍵即可。  如需詳細資訊，請參閱[建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)和 [如何：使用 Windows Form Label 控制項建立便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)。  
  
 標籤中所顯示的標題是包含在 <xref:System.Windows.Forms.Label.Text%2A> 屬性中。  <xref:System.Windows.Forms.Label.TextAlign%2A> 屬性可讓您設定標籤中文字的對齊。  如需詳細資訊，請參閱 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.Label>   
 [如何：調整 Windows Form Label 控制項大小以適合其內容](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [如何：使用 Windows Form Label 控制項建立便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)