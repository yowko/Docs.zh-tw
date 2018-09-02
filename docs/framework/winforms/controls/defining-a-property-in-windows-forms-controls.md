---
title: 定義 Windows Form 控制項中的屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: c21aee867fc78c55e62eb183bb1a12ebf1c472e8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425576"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>定義 Windows Form 控制項中的屬性
如需屬性的概觀，請參閱[屬性概觀](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)。 定義屬性時，有一些重要的考量︰  
  
-   您必須將屬性 (Attribute) 套用至您所定義的屬性 (Property)。 屬性 (Attribute) 指定設計工具如何顯示屬性 (Property)。 如需詳細資料，請參閱[元件的設計階段屬性](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)。  
  
-   如果變更的屬性會影響控制項的視覺顯示，請呼叫<xref:System.Windows.Forms.Control.Invalidate%2A>方法 (您的控制項繼承自<xref:System.Windows.Forms.Control>) 從`set`存取子。 <xref:System.Windows.Forms.Control.Invalidate%2A> 接著會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，以重新繪製控制項。 多次呼叫<xref:System.Windows.Forms.Control.Invalidate%2A>的單一呼叫會導致<xref:System.Windows.Forms.Control.OnPaint%2A>為了提高效率。  
  
-   .NET Framework Class Library 提供一般資料型別的轉換器，例如整數、十進位數字、布林值和其他型別。 型別轉換器的用途通常是將字串轉換成值 (從字串資料至其他資料型別)。 一般資料型別與預設型別轉換器相關聯，可將值轉換成字串，也可將字串轉換成適當的資料型別。 如果您定義的屬性 (Property) 是自訂 (亦即非標準) 資料型別，您必須套用屬性 (Attribute)，指定要與該屬性 (Property) 相關聯的型別轉換器。 您也可以使用屬性 (Attribute)，將自訂 UI 類型編輯器與屬性 (Property) 相關聯。 UI 類型編輯器提供使用者介面來編輯屬性或資料型別。 色彩選擇器是 UI 類型編輯器的一個例子。 本主題最後會提供屬性的範例。  
  
    > [!NOTE]
    >  如果型別轉換器或 UI 類型編輯器不適用於您的自訂屬性，您可以如[擴充設計階段支援](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)所述自行實作。  
  
 下列程式碼片段示範如何定義自訂控制項 `FlashTrackBar` 的自訂事件 `EndColor`。  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 下列程式碼片段將型別轉換器和 UI 類型編輯器與屬性 `Value` 相關聯。 在此情況下`Value`是一個整數，而具有預設型別轉換子，但<xref:System.ComponentModel.TypeConverterAttribute>屬性會套用自訂型別轉換子 (`FlashTrackBarValueConverter`)，可讓設計工具，以顯示成百分比。 UI 類型編輯器 `FlashTrackBarValueEditor` 可讓百分比以視覺化方式呈現。 此範例也顯示型別轉換器或所指定的編輯器<xref:System.ComponentModel.TypeConverterAttribute>或<xref:System.ComponentModel.EditorAttribute>屬性會覆寫預設轉換器。  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [使用 ShouldSerialize 和 Reset 方法定義預設值](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
