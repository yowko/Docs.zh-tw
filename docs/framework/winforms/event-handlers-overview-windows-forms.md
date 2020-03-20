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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141688"
---
# <a name="event-handlers-overview-windows-forms"></a>事件處理常式概觀 (Windows Form)
事件處理常式是綁定到事件的方法。 引發事件時，將執行事件處理常式中的代碼。 每個事件處理常式提供兩個參數，允許您正確處理事件。 下面的示例顯示了<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>事件的事件處理常式。  
  
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
  
 第一個參數`sender`提供引發事件的物件的引用。 在上面的示例中，`e`第二個參數傳遞特定于正在處理的事件的物件。 通過引用物件的屬性（有時，有時，其方法），可以獲取資訊，例如滑鼠的位置，用於滑鼠事件或在拖放事件中傳輸的資料。  
  
 通常，每個事件都會為第二個參數生成具有不同事件物件類型的事件處理常式。 某些事件處理常式（如<xref:System.Windows.Forms.Control.MouseDown>和<xref:System.Windows.Forms.Control.MouseUp>事件的事件處理常式）對於其第二個參數具有相同的物件類型。 對於這些類型的事件，可以使用同一事件處理常式來處理這兩個事件。  
  
 您還可以使用同一事件處理常式處理不同控制項的同一事件。 例如，如果表單上有一組<xref:System.Windows.Forms.RadioButton>控制項，則可以為<xref:System.Windows.Forms.Control.Click>事件創建單個事件處理常式，並將每個控制項<xref:System.Windows.Forms.Control.Click>的事件綁定到單個事件處理常式。 有關詳細資訊，請參閱[：將多個事件連接到 Windows 表單中的單個事件處理常式](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Forms 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)
- [事件概觀](events-overview-windows-forms.md)
