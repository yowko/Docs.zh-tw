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
ms.openlocfilehash: a641b1e7565842a1edf6aeec88bdc37ee0786ab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969122"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="a70ee-102">定義 Windows Form 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="a70ee-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="a70ee-103">如需屬性的概觀，請參閱[屬性概觀](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="a70ee-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="a70ee-104">定義屬性時，有一些重要的考量︰</span><span class="sxs-lookup"><span data-stu-id="a70ee-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="a70ee-105">您必須將屬性 (Attribute) 套用至您所定義的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a70ee-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="a70ee-106">屬性 (Attribute) 指定設計工具如何顯示屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a70ee-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="a70ee-107">如需詳細資料，請參閱[元件的設計階段屬性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="a70ee-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="a70ee-108">如果變更屬性會影響控制項的視覺顯示, 請從<xref:System.Windows.Forms.Control.Invalidate%2A> `set`存取子呼叫方法 (您的控制項所<xref:System.Windows.Forms.Control>繼承的)。</span><span class="sxs-lookup"><span data-stu-id="a70ee-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="a70ee-109"><xref:System.Windows.Forms.Control.Invalidate%2A>接著會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>方法, 這會重新繪製控制項。</span><span class="sxs-lookup"><span data-stu-id="a70ee-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="a70ee-110">針對效率, <xref:System.Windows.Forms.Control.Invalidate%2A>多次呼叫會導致單一呼叫。 <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="a70ee-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="a70ee-111">.NET Framework Class Library 提供一般資料型別的轉換器，例如整數、十進位數字、布林值和其他型別。</span><span class="sxs-lookup"><span data-stu-id="a70ee-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="a70ee-112">型別轉換器的用途通常是將字串轉換成值 (從字串資料至其他資料型別)。</span><span class="sxs-lookup"><span data-stu-id="a70ee-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="a70ee-113">一般資料型別與預設型別轉換器相關聯，可將值轉換成字串，也可將字串轉換成適當的資料型別。</span><span class="sxs-lookup"><span data-stu-id="a70ee-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="a70ee-114">如果您定義的屬性 (Property) 是自訂 (亦即非標準) 資料型別，您必須套用屬性 (Attribute)，指定要與該屬性 (Property) 相關聯的型別轉換器。</span><span class="sxs-lookup"><span data-stu-id="a70ee-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="a70ee-115">您也可以使用屬性 (Attribute)，將自訂 UI 類型編輯器與屬性 (Property) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="a70ee-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="a70ee-116">UI 類型編輯器提供使用者介面來編輯屬性或資料型別。</span><span class="sxs-lookup"><span data-stu-id="a70ee-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="a70ee-117">色彩選擇器是 UI 類型編輯器的一個例子。</span><span class="sxs-lookup"><span data-stu-id="a70ee-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="a70ee-118">本主題最後會提供屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="a70ee-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a70ee-119">如果型別轉換器或 UI 類型編輯器不適用於您的自訂屬性，您可以如[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))所述自行實作。</span><span class="sxs-lookup"><span data-stu-id="a70ee-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="a70ee-120">下列程式碼片段示範如何定義自訂控制項 `FlashTrackBar` 的自訂事件 `EndColor`。</span><span class="sxs-lookup"><span data-stu-id="a70ee-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="a70ee-121">下列程式碼片段將型別轉換器和 UI 類型編輯器與屬性 `Value` 相關聯。</span><span class="sxs-lookup"><span data-stu-id="a70ee-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="a70ee-122">在此情況`Value`下, 是一個整數而且具有預設類型轉換器, <xref:System.ComponentModel.TypeConverterAttribute>但是屬性會套用自訂類型轉換器`FlashTrackBarValueConverter`(), 讓設計工具將它顯示為百分比。</span><span class="sxs-lookup"><span data-stu-id="a70ee-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="a70ee-123">UI 類型編輯器 `FlashTrackBarValueEditor` 可讓百分比以視覺化方式呈現。</span><span class="sxs-lookup"><span data-stu-id="a70ee-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="a70ee-124">這個範例也會顯示由<xref:System.ComponentModel.TypeConverterAttribute>或<xref:System.ComponentModel.EditorAttribute>屬性所指定的型別轉換子或編輯器會覆寫預設的轉換器。</span><span class="sxs-lookup"><span data-stu-id="a70ee-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a70ee-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a70ee-125">See also</span></span>

- [<span data-ttu-id="a70ee-126">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="a70ee-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="a70ee-127">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="a70ee-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="a70ee-128">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="a70ee-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="a70ee-129">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="a70ee-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
