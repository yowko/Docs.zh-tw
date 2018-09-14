---
title: 如何：在 Windows Form 控制項中套用屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519597"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="072cd-102">如何：在 Windows Form 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="072cd-103">若要開發元件和控制項的設計環境中正確互動，並在執行階段會正確執行，您需要正確地將屬性套用至類別和成員。</span><span class="sxs-lookup"><span data-stu-id="072cd-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="072cd-104">範例</span><span class="sxs-lookup"><span data-stu-id="072cd-104">Example</span></span>  
 <span data-ttu-id="072cd-105">下列程式碼範例示範如何使用自訂控制項上的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="072cd-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="072cd-106">控制項將示範簡單的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="072cd-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="072cd-107">當控制項已繫結至資料來源時，它會顯示傳送中的資料來源的值<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="072cd-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="072cd-108">如果值超過所指定的值`Threshold`屬性，`ThresholdExceeded`就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="072cd-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="072cd-109">`AttributesDemoControl`記錄值`LogEntry`類別。</span><span class="sxs-lookup"><span data-stu-id="072cd-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="072cd-110">`LogEntry`類別是範本類別，這表示它所記錄的型別上參數化。</span><span class="sxs-lookup"><span data-stu-id="072cd-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="072cd-111">例如，如果`AttributesDemoControl`是記錄值的型別`float`，每個`LogEntry`宣告執行個體，然後使用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="072cd-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="072cd-112">因為`LogEntry`已參數化的任意型別，它必須使用反映來操作參數型別。</span><span class="sxs-lookup"><span data-stu-id="072cd-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="072cd-113">閾值項功能就能運作，參數型別`T`必須實作<xref:System.IComparable>介面。</span><span class="sxs-lookup"><span data-stu-id="072cd-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="072cd-114">表單裝載`AttributesDemoControl`定期查詢的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072cd-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="072cd-115">每個值封裝在`LogEntry`適當的類型，並加入表單的<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="072cd-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="072cd-116">`AttributesDemoControl`接收透過其資料繫結的值，並顯示在值<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="072cd-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="072cd-117">第一個程式碼範例是`AttributesDemoControl`實作。</span><span class="sxs-lookup"><span data-stu-id="072cd-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="072cd-118">第二個程式碼範例示範如何使用的表單`AttributesDemoControl`。</span><span class="sxs-lookup"><span data-stu-id="072cd-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="072cd-119">類別層級屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-119">Class-level Attributes</span></span>  
 <span data-ttu-id="072cd-120">有些屬性被套用在類別層級。</span><span class="sxs-lookup"><span data-stu-id="072cd-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="072cd-121">下列程式碼範例會顯示通常會套用至 Windows Form 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="072cd-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="072cd-122">TypeConverter 屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="072cd-123"><xref:System.ComponentModel.TypeConverterAttribute> 是另一個常用的類別層級屬性。</span><span class="sxs-lookup"><span data-stu-id="072cd-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="072cd-124">下列程式碼範例示範使用`LogEntry`類別。</span><span class="sxs-lookup"><span data-stu-id="072cd-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="072cd-125">此範例也會示範實作<xref:System.ComponentModel.TypeConverter>for`LogEntry`型別，稱為`LogEntryTypeConverter`。</span><span class="sxs-lookup"><span data-stu-id="072cd-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="072cd-126">成員層級屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-126">Member-level Attributes</span></span>  
 <span data-ttu-id="072cd-127">有些屬性是在成員層級套用。</span><span class="sxs-lookup"><span data-stu-id="072cd-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="072cd-128">下列程式碼範例示範一些通常會套用到 Windows Form 控制項的屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="072cd-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="072cd-129">AmbientValue 屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="072cd-130">下列範例示範<xref:System.ComponentModel.AmbientValueAttribute>而且顯示支援與設計環境互動的程式碼。</span><span class="sxs-lookup"><span data-stu-id="072cd-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="072cd-131">這種互動會呼叫*氣氛*。</span><span class="sxs-lookup"><span data-stu-id="072cd-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="072cd-132">資料繫結屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-132">Databinding Attributes</span></span>  
 <span data-ttu-id="072cd-133">下列範例示範複雜資料繫結的實作。</span><span class="sxs-lookup"><span data-stu-id="072cd-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="072cd-134">類別層級<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>、 顯示之前，指定`DataSource`和`DataMember`来用於資料繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="072cd-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="072cd-135"><xref:System.ComponentModel.AttributeProviderAttribute>指定的型別`DataSource`屬性會繫結。</span><span class="sxs-lookup"><span data-stu-id="072cd-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="072cd-136">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="072cd-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="072cd-137">裝載表單`AttributesDemoControl`需要參考`AttributesDemoControl`若要建置的組件。</span><span class="sxs-lookup"><span data-stu-id="072cd-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072cd-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="072cd-138">See Also</span></span>  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="072cd-139">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="072cd-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="072cd-140">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="072cd-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="072cd-141">如何： 序列化標準類型使用 DesignerSerializationVisibilityAttribute 的集合</span><span class="sxs-lookup"><span data-stu-id="072cd-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
