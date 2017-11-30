---
title: "如何：公開組成控制項的屬性"
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
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>如何：公開組成控制項的屬性
複合控制項所組成的控制項稱為*構成控制項*。 這些控制項通常宣告為私用，因此開發人員無法存取。 如果您想要讓未來的使用者可以使用這些控制項的屬性，您必須公開給使用者。 組成控制項的屬性由使用者控制項，以建立屬性，然後使用`get`和`set`該屬性的存取子中組成控制項的私用屬性的變更生效。  
  
 假設使用者控制項，請考慮使用構成按鈕名為`MyButton`。 在此範例中，當使用者要求`ConstituentButtonBackColor`屬性、 值儲存在<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`傳遞。 當使用者指派給這個屬性的值時，這個值自動傳遞給<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`和`set`會執行程式碼，變更的色彩`MyButton`。  
  
 下列範例示範如何公開<xref:System.Windows.Forms.Control.BackColor%2A>構成按鈕的屬性：  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>公開構成控制項的屬性  
  
1.  建立使用者控制項的公用屬性。  
  
2.  在`get`屬性，可擷取您想要公開的屬性值撰寫程式碼區段。  
  
3.  在`set`屬性，會將屬性的值傳遞給公開的屬性組成控制項撰寫程式碼區段。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.UserControl>  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
