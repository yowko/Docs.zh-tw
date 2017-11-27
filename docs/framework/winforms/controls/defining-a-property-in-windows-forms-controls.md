---
title: "定義 Windows Form 控制項中的屬性"
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
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c3c25b9c408e5b8f0b76cdf87375875cdb06a13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="17cc0-102">定義 Windows Form 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="17cc0-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="17cc0-103">如需屬性的概觀，請參閱[屬性概觀](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)。</span><span class="sxs-lookup"><span data-stu-id="17cc0-103">For an overview of properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="17cc0-104">定義屬性時，有一些重要的考量︰</span><span class="sxs-lookup"><span data-stu-id="17cc0-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="17cc0-105">您必須將屬性 (Attribute) 套用至您所定義的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="17cc0-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="17cc0-106">屬性 (Attribute) 指定設計工具如何顯示屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="17cc0-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="17cc0-107">如需詳細資料，請參閱[元件的設計階段屬性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)。</span><span class="sxs-lookup"><span data-stu-id="17cc0-107">For details, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
-   <span data-ttu-id="17cc0-108">屬性變更會影響控制項的視覺顯示，如果呼叫<xref:System.Windows.Forms.Control.Invalidate%2A>方法 (控制項繼承自<xref:System.Windows.Forms.Control>) 從`set`存取子。</span><span class="sxs-lookup"><span data-stu-id="17cc0-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="17cc0-109"><xref:System.Windows.Forms.Control.Invalidate%2A>依序呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，這個方法會重新繪製控制項。</span><span class="sxs-lookup"><span data-stu-id="17cc0-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="17cc0-110">多個呼叫<xref:System.Windows.Forms.Control.Invalidate%2A>導致呼叫一次<xref:System.Windows.Forms.Control.OnPaint%2A>為了提高效率。</span><span class="sxs-lookup"><span data-stu-id="17cc0-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="17cc0-111">.NET Framework Class Library 提供一般資料型別的轉換器，例如整數、十進位數字、布林值和其他型別。</span><span class="sxs-lookup"><span data-stu-id="17cc0-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="17cc0-112">型別轉換器的用途通常是將字串轉換成值 (從字串資料至其他資料型別)。</span><span class="sxs-lookup"><span data-stu-id="17cc0-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="17cc0-113">一般資料型別與預設型別轉換器相關聯，可將值轉換成字串，也可將字串轉換成適當的資料型別。</span><span class="sxs-lookup"><span data-stu-id="17cc0-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="17cc0-114">如果您定義的屬性 (Property) 是自訂 (亦即非標準) 資料型別，您必須套用屬性 (Attribute)，指定要與該屬性 (Property) 相關聯的型別轉換器。</span><span class="sxs-lookup"><span data-stu-id="17cc0-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="17cc0-115">您也可以使用屬性 (Attribute)，將自訂 UI 類型編輯器與屬性 (Property) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="17cc0-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="17cc0-116">UI 類型編輯器提供使用者介面來編輯屬性或資料型別。</span><span class="sxs-lookup"><span data-stu-id="17cc0-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="17cc0-117">色彩選擇器是 UI 類型編輯器的一個例子。</span><span class="sxs-lookup"><span data-stu-id="17cc0-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="17cc0-118">本主題最後會提供屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="17cc0-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17cc0-119">如果型別轉換器或 UI 類型編輯器不適用於您的自訂屬性，您可以如[擴充設計階段支援](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)所述自行實作。</span><span class="sxs-lookup"><span data-stu-id="17cc0-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
 <span data-ttu-id="17cc0-120">下列程式碼片段示範如何定義自訂控制項 `FlashTrackBar` 的自訂事件 `EndColor`。</span><span class="sxs-lookup"><span data-stu-id="17cc0-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="17cc0-121">下列程式碼片段將型別轉換器和 UI 類型編輯器與屬性 `Value` 相關聯。</span><span class="sxs-lookup"><span data-stu-id="17cc0-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="17cc0-122">在此情況下`Value`是一個整數，有的預設型別轉換子，但<xref:System.ComponentModel.TypeConverterAttribute>屬性會套用自訂類型轉換器 (`FlashTrackBarValueConverter`)，可讓設計工具，以顯示成百分比。</span><span class="sxs-lookup"><span data-stu-id="17cc0-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="17cc0-123">UI 類型編輯器 `FlashTrackBarValueEditor` 可讓百分比以視覺化方式呈現。</span><span class="sxs-lookup"><span data-stu-id="17cc0-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="17cc0-124">此範例也顯示型別轉換子或所指定的編輯器<xref:System.ComponentModel.TypeConverterAttribute>或<xref:System.ComponentModel.EditorAttribute>屬性會覆寫預設的轉換器。</span><span class="sxs-lookup"><span data-stu-id="17cc0-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17cc0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17cc0-125">See Also</span></span>  
 [<span data-ttu-id="17cc0-126">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="17cc0-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="17cc0-127">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="17cc0-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [<span data-ttu-id="17cc0-128">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="17cc0-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [<span data-ttu-id="17cc0-129">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="17cc0-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
