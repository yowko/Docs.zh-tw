---
title: 作法：公開組成控制項的屬性
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
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015884"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>HOW TO：公開組成控制項的屬性
組成複合控制項的控制項稱為「*組成控制項*」。 這些控制項通常會宣告為私用, 因此開發人員無法存取。 如果您想要讓這些控制項的屬性可供未來的使用者使用, 您必須將它們公開給使用者。 組成控制項的屬性會藉由在使用者控制項中建立屬性來公開, 並使用該屬性`get`的`set`和存取子來影響組成控制項之私用屬性的變更。

 假設有一個具有名為`MyButton`之組成按鈕的假設使用者控制項。 在此範例中, 當使用者要求`ConstituentButtonBackColor`屬性時, 會傳遞儲存<xref:System.Windows.Forms.Control.BackColor%2A>在之`MyButton`屬性中的值。 當使用者將值指派給這個屬性時, 該值會自動傳遞<xref:System.Windows.Forms.Control.BackColor%2A>至的`MyButton`屬性, 而程式`set` `MyButton`代碼將會執行, 並變更的色彩。

 下列範例顯示如何公開<xref:System.Windows.Forms.Control.BackColor%2A> [構成] 按鈕的屬性:

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

### <a name="to-expose-a-property-of-a-constituent-control"></a>公開組成控制項的屬性

1. 建立使用者控制項的公用屬性。

2. 在屬性的區段中, 撰寫程式碼來抓取您想要公開之屬性的值。 `get`

3. 在屬性`set`的區段中, 撰寫程式碼, 將屬性的值傳遞給組成控制項的公開屬性。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- [Windows Forms 控制項中的屬性](properties-in-windows-forms-controls.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
