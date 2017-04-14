---
title: "鍵盤輸入的運作方式 | Microsoft Docs"
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
  - "鍵盤輸入, 關於鍵盤輸入"
  - "鍵盤, 鍵盤輸入"
  - "Windows Form, 鍵盤輸入"
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 鍵盤輸入的運作方式
Windows Form 會引發回應 Windows 訊息的鍵盤事件，以處理鍵盤輸入。  大部分的 Windows Form 應用程式都是經由處理鍵盤事件來處理鍵盤輸入。  但是，你必須了解鍵盤訊息的運作方式，才能實作更進階的鍵盤輸入案例，例如在按鍵到達控制項之前加以攔截。  本主題描述 Windows Form 所識別的按鍵資料型別，並提供鍵盤訊息的路由方式概觀。  如需鍵盤事件的詳細資訊，請參閱[使用鍵盤事件](../../../docs/framework/winforms/using-keyboard-events.md)。  
  
## 按鍵的型別  
 Windows Form 會將鍵盤輸入識別為由位元 <xref:System.Windows.Forms.Keys> 列舉型別所表示的虛擬按鍵碼 \(Virtual Key Code\)。  透過 <xref:System.Windows.Forms.Keys> 列舉型別，您可以組合一系列的按鍵來產生一個值。  這些值會對應至伴隨 WM\_KEYDOWN 和 WM\_SYSKEYDOWN Windows 訊息的值。  您可以透過處理 <xref:System.Windows.Forms.Control.KeyDown> 或 <xref:System.Windows.Forms.Control.KeyUp> 事件，偵測大部分按下的實體鍵。  字元鍵是 <xref:System.Windows.Forms.Keys> 列舉型別的子集，並對應至伴隨 WM\_CHAR 和 WM\_SYSCHAR Windows 訊息的值。  如果按下的按鍵組合會產生一個字元，您可以處理 <xref:System.Windows.Forms.Control.KeyPress> 事件來偵測該字元。  或者，您可以使用由 Visual Basic 程式設計介面所公開的 <xref:Microsoft.VisualBasic.Devices.Keyboard>，探索已按下哪些按鍵並傳送這些按鍵。  如需詳細資訊，請參閱[Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md)。  
  
## 鍵盤事件的順序  
 如前面所列，有 3 個會在控制項上發生的鍵盤相關事件。  下列順序顯示一般的事件順序：  
  
1.  使用者按下 "a" 按鍵，前置處理、分派按鍵，然後發生 <xref:System.Windows.Forms.Control.KeyDown> 事件。  
  
2.  使用者按住 "a" 按鍵，前置處理、分派按鍵，然後發生 <xref:System.Windows.Forms.Control.KeyPress> 事件。  
  
     這個事件會在使用者按住按鍵時發生多次。  
  
3.  使用者放開 "a" 按鍵，前置處理、分派按鍵，然後發生 <xref:System.Windows.Forms.Control.KeyUp> 事件。  
  
## 前置處理按鍵  
 不像其他訊息，鍵盤訊息會在表單或控制項的 <xref:System.Windows.Forms.Control.WndProc%2A> 方法中進行處理。  但是，在處理鍵盤訊息之前，<xref:System.Windows.Forms.Control.PreProcessMessage%2A> 方法會呼叫一或多個方法，這些方法可以被覆寫以處理特殊的字元鍵和實體鍵。  在控制項處理訊息之前，您可以覆寫這些方法以偵測和篩選某些按鍵。  下表顯示所執行的動作和出現的相關方法 \(以方法出現的順序排列\)。  
  
### KeyDown 事件的前置處理  
  
|動作|相關方法|備註|  
|--------|----------|--------|  
|檢查命令鍵，例如快速鍵或功能表捷徑。|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|這個方法會在處理一般按鍵之前，先處理命令鍵。  如果這個方法傳回 `true`，不會分派按鍵訊息，而且不會發生按鍵事件。  如果傳回 `false`，會呼叫 <xref:System.Windows.Forms.Control.IsInputKey%2A>`.`|  
|檢查是否為需要前置處理的特殊按鍵，或者為應該引發 <xref:System.Windows.Forms.Control.KeyDown> 事件並分派給控制項的一般字元按鍵。|<xref:System.Windows.Forms.Control.IsInputKey%2A>|如果方法傳回 `true`，表示控制項為一般字元並引發 <xref:System.Windows.Forms.Control.KeyDown> 事件。  如果傳回 `false`，會呼叫 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>。 **Note:**  若要確保控制項取得按鍵或組合鍵，您可以處理 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件，並為您想要的按鍵將 <xref:System.Windows.Forms.PreviewKeyDownEventArgs> 的 <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> 設定為 `true`。|  
|檢查是否為巡覽鍵 \(ESC、TAB、ENTER 或方向鍵\)。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|這個方法會處理利用控制項中特殊功能的實體鍵，例如在控制項和其父代之間切換焦點。  如果直接相關的控制項沒有處理按鍵，便會由父控制項呼叫 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>，以此類推，直到階層架構中的最上層控制項為止。  如果這個方法傳回 `true`，便會完成前置處理，並且不會產生按鍵事件。  如果傳回 `false`，則會發生 <xref:System.Windows.Forms.Control.KeyDown> 事件。|  
  
### KeyPress 事件的前置處理  
  
|動作|相關方法|備註|  
|--------|----------|--------|  
|查看按鍵是否為應該由控制項處理的一般字元。|<xref:System.Windows.Forms.Control.IsInputChar%2A>|如果字元為一般字元，這個方法會傳回 `true`，並引發 <xref:System.Windows.Forms.Control.KeyPress> 事件，而且不會發生進一步的前置處理。  否則會呼叫 <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>。|  
|查看字元是否為助憶鍵，例如按鈕上的 \[確定\(&O\)\]。|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|這個方法類似 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>，會沿著控制項階層架構向上呼叫。  如果控制項是容器控制項，則會在控制項本身和其子控制項上呼叫 <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>，以檢查助憶鍵。  如果 <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> 傳回 `true`，不會發生 <xref:System.Windows.Forms.Control.KeyPress> 事件。|  
  
## 處理鍵盤訊息  
 在鍵盤訊息到達表單或控制項上的 <xref:System.Windows.Forms.Control.WndProc%2A> 方法後，會由可以被覆寫的一組方法進行處理。  這些方法中的每一個都會傳回 <xref:System.Boolean> 值，指定鍵盤訊息是否已經由控制項處理和使用。  如果其中一個方法傳回 `true`，會認為訊息已經處理，並且不會再傳入控制項的基底或父代做進一步的處理。  否則，訊息會停留在訊息佇列中，並且可能會由控制項的基底或父代中的另一個方法處理。  下表顯示會處理鍵盤訊息的方法：  
  
|方法|備註|  
|--------|--------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|這個方法會處理由控制項的 <xref:System.Windows.Forms.Control.WndProc%2A> 方法所收到的所有鍵盤訊息。|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|這個方法會將鍵盤訊息傳送到控制項的父代。  如果 <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> 傳回 `true`，便不會產生按鍵事件；否則會呼叫 <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>。|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|這個方法會適當地引發 <xref:System.Windows.Forms.Control.KeyDown>、<xref:System.Windows.Forms.Control.KeyPress> 和 <xref:System.Windows.Forms.Control.KeyUp> 事件。|  
  
## 覆寫鍵盤方法  
 當鍵盤訊息在處理中和已處理時，有許多可以進行覆寫的方法；但是其中有些方法是較好的選擇。  下表顯示您可能想要完成的工作，以及覆寫鍵盤方法的最佳方式。  如需覆寫方法的詳細資訊，請參閱[NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)。  
  
|工作|方法|  
|--------|--------|  
|攔截巡覽鍵並引發 <xref:System.Windows.Forms.Control.KeyDown> 事件。  例如，您想要在文字方塊中處理 TAB 和 Enter 鍵。|覆寫 <xref:System.Windows.Forms.Control.IsInputKey%2A>。 **Note:**  或是，您可以處理 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件，並且針對您想要的按鍵將 <xref:System.Windows.Forms.PreviewKeyDownEventArgs> 的 <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> 設定為 `true`。|  
|在控制項上執行特殊輸入或巡覽處理。  例如，您想要在清單控制項中使用方向鍵來變更選取的項目。|覆寫 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|攔截巡覽鍵並引發 <xref:System.Windows.Forms.Control.KeyPress> 事件。  例如，在微調方塊控制項中，您想要按下多個方向鍵時可以在項目中加速前進。|覆寫 <xref:System.Windows.Forms.Control.IsInputChar%2A>。|  
|在 <xref:System.Windows.Forms.Control.KeyPress> 事件中執行特殊輸入或巡覽處理。  例如，在清單控制項中，按住 "r" 按鍵時可以跳過其他項目並到達以 r 字母開頭的項目。|覆寫 <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|執行自訂的助憶鍵處理；例如，您想要在工具列所包含的主控描繪 \(Owner\-Drawn\) 按鈕上處理助憶鍵。|覆寫 <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>|  
  
## 請參閱  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.WndProc%2A>   
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>   
 [My.Computer.Keyboard Object](../../../ocs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)   
 [Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md)   
 [使用鍵盤事件](../../../docs/framework/winforms/using-keyboard-events.md)