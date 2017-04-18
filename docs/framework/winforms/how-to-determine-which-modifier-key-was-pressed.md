---
title: "如何：判斷所按的輔助按鍵為何 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "alt 鍵"
  - "control 鍵"
  - "事件 [Windows Form], 鍵盤"
  - "事件 [Windows Form], 滑鼠"
  - "鍵盤輸入"
  - "鍵盤, 鍵盤輸入"
  - "索引鍵, alt 鍵"
  - "索引鍵, control 鍵"
  - "索引鍵, 判斷上次按下的"
  - "索引鍵, 輔助按鍵"
  - "索引鍵, shift 鍵"
  - "Keys.Alt 列舉類型成員"
  - "Keys.ControlKey 列舉類型成員"
  - "Keys.Shift 列舉類型成員"
  - "輔助按鍵"
  - "shift 鍵"
  - "使用者輸入, 檢查鍵盤"
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：判斷所按的輔助按鍵為何
建立接受使用者按鍵輸入的應用程式時，您可能也會想要監視輔助按鍵 \(Modifier Key\)，例如 SHIFT、ALT 和 CTRL 鍵。  當按下輔助按鍵與其他按鍵或滑鼠按鍵的組合時，應用程式可以適當地回應。  例如，如果是按下字母 S，只會單純在螢幕上顯示 "s"，但如果是按下 CTRL\+S 則會儲存目前的文件。  如果您處理 <xref:System.Windows.Forms.Control.KeyDown> 事件，則事件處理常式所接收的 <xref:System.Windows.Forms.KeyEventArgs> 其 <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> 屬性會指定所按下的輔助按鍵為何。  或者，<xref:System.Windows.Forms.KeyEventArgs> 的 <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> 屬性會指定，和位元 OR 結合的任一輔助按鍵是與哪個字母一起按下。  但是，如果您處理的是 <xref:System.Windows.Forms.Control.KeyPress> 事件或滑鼠事件，則事件處理常式不會接收這個資訊。  在這種情況下，您必須使用 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.ModifierKeys%2A> 屬性。  不論是哪一種情況下，您都必須執行適當 <xref:System.Windows.Forms.Keys> 值的位元 AND 以及正在測試的值。  <xref:System.Windows.Forms.Keys> 列舉型別提供每個輔助按鍵的變異，所以請您務必以正確值執行位元 AND。  例如，SHIFT 鍵是以 <xref:System.Windows.Forms.Keys>、<xref:System.Windows.Forms.Keys>、<xref:System.Windows.Forms.Keys> 和 <xref:System.Windows.Forms.Keys> 表示，而測試 SHIFT 是否為輔助按鍵的正確值則是 <xref:System.Windows.Forms.Keys>。  同樣地，若要測試 CTLR 和 ALT 是否為輔助按鍵，則您應分別使用 <xref:System.Windows.Forms.Keys> 和 <xref:System.Windows.Forms.Keys> 值。  
  
> [!NOTE]
>  Visual Basic 程式設計人員也可以透過 <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> 屬性存取按鍵資訊。  
  
### 若要判斷所按輔助按鍵為何  
  
-   若要判斷所按的特定輔助按鍵為何，請以 <xref:System.Windows.Forms.Control.ModifierKeys%2A> 屬性和 <xref:System.Windows.Forms.Keys> 列舉值來使用位元 `AND` 運算子。  下列程式碼範例會示範如何判斷在 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式內是否有按下 SHIFT 鍵。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## 請參閱  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>   
 [Windows Form 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [How to: Determine If CapsLock is On in Visual Basic](http://msdn.microsoft.com/zh-tw/91e60f5c-dd61-4222-ba5f-39af803afd8c)