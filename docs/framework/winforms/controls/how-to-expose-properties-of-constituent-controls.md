---
title: "如何：公開組成控制項的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "組成控制項"
  - "控制項 [Windows Form], 組成"
  - "自訂控制項 [Windows Form], 公開屬性"
  - "使用者控制項 [Windows Form], 公開構成控制項"
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：公開組成控制項的屬性
組成複合控制項 \(Composite Control\) 的控制項稱為*組成控制項*。  這些控制項通常是宣告為私用的 \(Private\)，因此開發人員無法存取。  如果您希望未來使用者能夠使用這些控制項的屬性，必須將屬性公開給使用者。  若要公開組成控制項的屬性，您可在使用者控制項中建立屬性，並使用這個屬性的 `get` 和 `set` 存取子來使組成控制項的私用屬性中的變更生效。  
  
 假設某個使用者控制項有一個名為 `MyButton` 的組成按鈕。  在這個範例中，當使用者要求 `ConstituentButtonBackColor` 屬性時，就會傳遞儲存在 `MyButton` 的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性中的值。  當使用者將值指派給這個屬性時，會將這個值自動傳遞至 `MyButton` 的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性，並將執行 `set` 程式碼，變更 `MyButton` 的色彩。  
  
 下面的範例顯示如何公開組成按鈕的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性：  
  
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
  
### 若要公開組成控制項的屬性  
  
1.  為使用者控制項建立公用屬性。  
  
2.  在屬性的 `get` 區段，寫入可擷取您要公開的屬性值的程式碼。  
  
3.  在屬性的 `set` 區段，寫入將屬性值傳遞到組成控制項的公開屬性的程式碼。  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl>   
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)