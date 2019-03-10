---
title: 事件處理常式概觀 (Windows Form)
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
ms.openlocfilehash: 6dbcffadfd484dc33db2fcd3ee3f680dcc0740e5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703383"
---
# <a name="event-handlers-overview-windows-forms"></a>事件處理常式概觀 (Windows Form)
事件處理常式是繫結至事件的方法。 當引發事件時，會執行內的事件處理常式的程式碼。 每個事件處理常式提供可讓您正確地處理事件的兩個參數。 下列範例顯示的事件處理常式<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件。  
  
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
  
 第一個參數，`sender`，提供引發事件之物件的參考。 第二個參數， `e`，在上述範例中，會傳遞物件特定處理的事件。 藉由參考物件的屬性 （和，某些情況下，其方法），您可以取得資訊，例如滑鼠事件或資料傳輸在拖放事件中的滑鼠位置。  
  
 通常每個事件，就會產生與第二個參數的不同事件物件類型的事件處理常式。 事件處理常式，如<xref:System.Windows.Forms.Control.MouseDown>和<xref:System.Windows.Forms.Control.MouseUp>事件，都有相同的物件類型，其第二個參數。 針對這些類型的事件，您可以使用相同的事件處理常式來處理這兩個事件。  
  
 您也可以使用相同的事件處理常式來處理不同的控制項相同的事件。 比方說，如果您有一群<xref:System.Windows.Forms.RadioButton>表單上的控制項，您可以建立單一事件處理常式<xref:System.Windows.Forms.Control.Click>事件，而且有每個控制項<xref:System.Windows.Forms.Control.Click>事件繫結至單一事件處理常式。 如需詳細資訊，請參閱[如何：將多個事件連線至 Windows Forms 中的單一事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱
- [在 Windows Forms 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件概觀](events-overview-windows-forms.md)
