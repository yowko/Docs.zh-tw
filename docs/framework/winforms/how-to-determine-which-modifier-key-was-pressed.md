---
title: "如何：判斷所按的輔助按鍵為何"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5f749d22c09d166e81ea08068f760f24960ec83
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>如何：判斷所按的輔助按鍵為何
當您建立應用程式可接受使用者按鍵輸入時，您可能也要監視輔助按鍵，例如 SHIFT、 ALT 和 CTRL 鍵。 與其他按鍵或滑鼠按鍵組合是按下輔助按鍵，您的應用程式能夠適當地回應。 例如，如果按下的代號 S 時，這只會出現在畫面上，"s"，但如果按下 CTRL + S 鍵的索引鍵，可能會儲存目前文件。 如果您處理<xref:System.Windows.Forms.Control.KeyDown>事件，<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>接收到事件處理常式會指定哪些輔助按鍵按下按鍵。 或者，<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>指定已按下也與位元 OR 運算結合任何輔助按鍵的字元。 不過，如果您要處理<xref:System.Windows.Forms.Control.KeyPress>事件或滑鼠事件，事件處理常式不會收到這項資訊。 在此情況下，您必須使用<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性<xref:System.Windows.Forms.Control>類別。 在任一情況下，您必須執行的適當位元 AND<xref:System.Windows.Forms.Keys>值以及您要測試的值。 <xref:System.Windows.Forms.Keys>列舉型別提供變化的每個輔助按鍵，因此是很重要，您執行位元，並使用正確的值。 SHIFT 鍵由例如<xref:System.Windows.Forms.Keys.Shift>， <xref:System.Windows.Forms.Keys.ShiftKey>，<xref:System.Windows.Forms.Keys.RShiftKey>和<xref:System.Windows.Forms.Keys.LShiftKey>測試 SHIFT 修飾詞的索引鍵是正確的值<xref:System.Windows.Forms.Keys.Shift>。 同樣地，若要測試 CTLR 和 ALT 修飾詞為您應該使用<xref:System.Windows.Forms.Keys.Control>和<xref:System.Windows.Forms.Keys.Alt>分別值。  
  
> [!NOTE]
>  Visual Basic 程式設計人員也可以存取金鑰資訊透過<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>屬性  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>若要判斷哪些輔助按鍵  
  
-   使用位元`AND`運算子搭配<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性和值的<xref:System.Windows.Forms.Keys>列舉型別來判斷是否要按下特定輔助按鍵。 下列程式碼範例示範如何判斷是否內按下 SHIFT 鍵<xref:System.Windows.Forms.Control.KeyPress>事件處理常式。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Windows Forms 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [如何： 判斷 CapsLock 是否在中，在 Visual Basic 中](http://msdn.microsoft.com/library/91e60f5c-dd61-4222-ba5f-39af803afd8c)
