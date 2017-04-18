---
title: "定義 Windows Form 控制項中的屬性 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 在程式碼中定義屬性"
  - "屬性 [Windows Form], 在程式碼中定義"
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 定義 Windows Form 控制項中的屬性
如需屬性的概觀，請參閱[屬性概觀](../Topic/Properties%20Overview.md)。  在定義屬性時有一些重要的考量：  
  
-   您必須套用屬性 \(Attribute\) 於您定義的屬性 \(Property\)。  屬性 \(Attribute\) 指定設計工具應該如何顯示屬性 \(Property\)。  如需詳細資訊，請參閱[元件的設計階段屬性](../Topic/Design-Time%20Attributes%20for%20Components.md)。  
  
-   如果變更屬性會影響控制項的視覺顯示，請從 `set` 存取子呼叫 <xref:System.Windows.Forms.Control.Invalidate%2A> 方法 \(您控制項繼承自 <xref:System.Windows.Forms.Control> 的方法\)。  <xref:System.Windows.Forms.Control.Invalidate%2A> 接著呼叫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，這將會重繪控制項。  對 <xref:System.Windows.Forms.Control.Invalidate%2A> 的多重呼叫為了有效率起見，會產生對 <xref:System.Windows.Forms.Control.OnPaint%2A> 的單一呼叫。  
  
-   .NET Framework 類別庫 \(Class Library\) 提供型別轉換子 \(Type Converter\) 給一般資料型別，例如整數、小數數字、布林 \(Boolean\) 值等。  型別轉換子的用途通常提供字串至數值的轉換 \(從字串資料至其他資料型別\)。  一般資料型別與預設型別轉換子有關聯，這轉換子會轉換數值為字串，和轉換字串為適當資料型別。  如果您定義自訂 \(亦即，非標準的\) 資料型別的屬性 \(Property\)，您將必須套用屬性 \(Attribute\)，以指定與那屬性相關的型別轉換子。  您可以也可以使用屬性 \(Attribute\) 來將自訂 UI 型別編輯器與屬性 \(Property\) 產生關聯。  UI 型別編輯器提供用以編輯屬性或資料型別的使用者介面。  色彩選擇器即為 UI 型別編輯器的一個例子。  屬性的範例在這個主題的結尾會提供。  
  
    > [!NOTE]
    >  如果您的自訂屬性沒有型別轉換子或 UI 型別編輯器，您可以實作一個，如[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md) 中所說明的。  
  
 下列程式碼片段為自訂控制項 `FlashTrackBar` 定義名為 `EndColor` 的自訂屬性。  
  
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
  
 下列程式碼片段將型別轉換子和 UI 型別編輯器與屬性 `Value` 產生關聯。  這個案例中，`Value` 為整數，並具有預設型別轉換子，但 <xref:System.ComponentModel.TypeConverterAttribute> 屬性套用自訂型別轉換子 \(`FlashTrackBarValueConverter`\) 以允許設計工具將它顯示為百分比。  UI 型別編輯器 `FlashTrackBarValueEditor` 讓百分比可以視覺化顯示。  這個範例也示範 <xref:System.ComponentModel.TypeConverterAttribute> 或 <xref:System.ComponentModel.EditorAttribute> 屬性指定的型別轉換子或編輯器如何覆寫預設轉換子。  
  
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
  
## 請參閱  
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [使用 ShouldSerialize 和 Reset 方法定義預設值](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)   
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)   
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)