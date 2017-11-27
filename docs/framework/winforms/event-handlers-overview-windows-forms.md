---
title: "事件處理常式概觀 (Windows Form)"
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
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>事件處理常式概觀 (Windows Form)
事件處理常式會是繫結至事件的方法。 當事件引發時，事件處理常式中的程式碼會執行。 每個事件處理常式提供可讓您正確處理事件的兩個參數。 下列範例顯示的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 第一個參數，`sender`，提供引發事件之物件的參考。 第二個參數， `e`，在上述範例中，會傳遞物件特定事件的處理。 藉由參考物件的屬性 （甚至是某些情況下，它的方法），您可以取得資訊，例如滑鼠事件或拖放事件中傳送的資料的滑鼠位置。  
  
 通常每個事件，就會產生具有不同的事件物件類型的第二個參數的事件處理常式。 事件處理常式，例如用於<xref:System.Windows.Forms.Control.MouseDown>和<xref:System.Windows.Forms.Control.MouseUp>事件，都有相同的物件類型，其第二個參數。 針對這些類型的事件，您可以使用相同的事件處理常式來處理這兩個事件。  
  
 您也可以使用相同的事件處理常式來處理不同的控制項相同的事件。 例如，如果您有一組<xref:System.Windows.Forms.RadioButton>表單上的控制項，您可以建立單一事件處理常式<xref:System.Windows.Forms.Control.Click>事件，而且有每個控制項<xref:System.Windows.Forms.Control.Click>事件繫結至單一事件處理常式。 如需詳細資訊，請參閱[如何： 連接至 Windows Form 中的單一事件處理常式的多個事件](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Windows Forms 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [事件概觀](../../../docs/framework/winforms/events-overview-windows-forms.md)
