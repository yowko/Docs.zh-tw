---
title: HOW TO：公開組成控制項的屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: 44b96218e674c754a1985f2f22a36707cd1776b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941371"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>HOW TO：公開組成控制項的屬性
組成複合控制項的控制項稱為*組成控制項*。 這些控制項通常宣告為私用，因此開發人員無法存取。 如果您想要讓未來的使用者都可以使用這些控制項的屬性，您必須將它們公開給使用者。 組成控制項的屬性會公開在使用者控制項中，建立屬性，並使用`get`和`set`該屬性的存取子中組成控制項的私用屬性的變更生效。  
  
 假設使用者控制項，請考慮組成的按鈕名為`MyButton`。 在此範例中，使用者要求時`ConstituentButtonBackColor`屬性中中, 儲存的值<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`傳遞。 當使用者指派給這個屬性的值時，該值會自動傳遞給<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`並`set`程式碼會執行變更的色彩`MyButton`。  
  
 下列範例示範如何公開<xref:System.Windows.Forms.Control.BackColor%2A>屬性構成的按鈕：  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>若要公開組成控制項的屬性  
  
1. 建立您的使用者控制項的公用屬性。  
  
2. 在 `get`區段的屬性，撰寫程式碼，擷取您想要公開之屬性的值。  
  
3. 在 `set`屬性，也就是撰寫程式碼，將屬性的值傳遞給公開組成控制項的屬性區段。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- [Windows Forms 控制項中的屬性](properties-in-windows-forms-controls.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
