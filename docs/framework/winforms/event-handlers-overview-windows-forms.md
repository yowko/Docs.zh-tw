---
title: 事件處理常式概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743466"
---
# <a name="event-handlers-overview-windows-forms"></a>事件處理常式概觀 (Windows Form)
事件處理常式是系結至事件的方法。 當引發事件時，就會執行事件處理常式中的程式碼。 每個事件處理常式都會提供兩個參數，讓您可以正確地處理事件。 下列範例顯示 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件的事件處理常式。  
  
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
  
 第一個參數（`sender`）會提供引發事件之物件的參考。 在上述範例中，第二個參數 `e`，會傳遞所處理事件的特定物件。 藉由參考物件的屬性（有時也是其方法），您可以取得資訊，例如滑鼠事件的位置，或在拖放事件中傳送的資料。  
  
 一般來說，每個事件都會針對第二個參數產生事件處理常式，並具有不同的事件物件類型。 某些事件處理常式，例如 <xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件的處理常式，其第二個參數具有相同的物件類型。 針對這些類型的事件，您可以使用相同的事件處理常式來處理這兩個事件。  
  
 您也可以使用相同的事件處理常式，針對不同的控制項處理相同的事件。 例如，如果您在表單上有一組 <xref:System.Windows.Forms.RadioButton> 控制項，您可以為 <xref:System.Windows.Forms.Control.Click> 事件建立單一事件處理常式，並讓每個控制項的 <xref:System.Windows.Forms.Control.Click> 事件系結至單一事件處理常式。 如需詳細資訊，請參閱[如何：將多個事件連接到 Windows Forms 中的單一事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Form 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件概觀](events-overview-windows-forms.md)
