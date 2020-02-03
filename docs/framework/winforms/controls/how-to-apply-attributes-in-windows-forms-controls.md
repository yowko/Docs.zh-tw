---
title: 在控制項中套用屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741487"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="9620a-102">如何：在 Windows Form 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="9620a-103">若要開發與設計環境正確互動並在執行時間正確執行的元件和控制項，您需要將屬性正確地套用至類別和成員。</span><span class="sxs-lookup"><span data-stu-id="9620a-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9620a-104">範例</span><span class="sxs-lookup"><span data-stu-id="9620a-104">Example</span></span>  
 <span data-ttu-id="9620a-105">下列程式碼範例示範如何在自訂控制項上使用多個屬性。</span><span class="sxs-lookup"><span data-stu-id="9620a-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="9620a-106">此控制項會示範簡單的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="9620a-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="9620a-107">當控制項系結至資料來源時，它會在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料來源所傳送的值。</span><span class="sxs-lookup"><span data-stu-id="9620a-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9620a-108">如果值超過 `Threshold` 屬性所指定的值，就會引發 `ThresholdExceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="9620a-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="9620a-109">`AttributesDemoControl` 會記錄具有 `LogEntry` 類別的值。</span><span class="sxs-lookup"><span data-stu-id="9620a-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="9620a-110">`LogEntry` 類別是樣板類別，這表示它會在其所記錄的類型上進行參數化。</span><span class="sxs-lookup"><span data-stu-id="9620a-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="9620a-111">例如，如果 `AttributesDemoControl` 是記錄 `float`類型的值，則每個 `LogEntry` 實例都會宣告並使用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9620a-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="9620a-112">因為 `LogEntry` 是由任意型別參數化，所以它必須使用反映來指令引數型別。</span><span class="sxs-lookup"><span data-stu-id="9620a-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="9620a-113">若要讓 [臨界值] 功能正常執行，參數類型 `T` 必須實 <xref:System.IComparable> 介面。</span><span class="sxs-lookup"><span data-stu-id="9620a-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="9620a-114">裝載 `AttributesDemoControl` 的表單會定期查詢效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9620a-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="9620a-115">每個值都封裝在適當類型的 `LogEntry` 中，並加入表單的 <xref:System.Windows.Forms.BindingSource>中。</span><span class="sxs-lookup"><span data-stu-id="9620a-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="9620a-116">`AttributesDemoControl` 會透過其資料系結接收值，並在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示值。</span><span class="sxs-lookup"><span data-stu-id="9620a-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="9620a-117">第一個程式碼範例是 `AttributesDemoControl` 的執行。</span><span class="sxs-lookup"><span data-stu-id="9620a-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="9620a-118">第二個程式碼範例示範使用 `AttributesDemoControl`的表單。</span><span class="sxs-lookup"><span data-stu-id="9620a-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="9620a-119">類別層級屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-119">Class-level Attributes</span></span>  
 <span data-ttu-id="9620a-120">某些屬性會在類別層級套用。</span><span class="sxs-lookup"><span data-stu-id="9620a-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="9620a-121">下列程式碼範例顯示常用於 Windows Forms 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="9620a-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="9620a-122">TypeConverter 屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="9620a-123"><xref:System.ComponentModel.TypeConverterAttribute> 是另一個常用的類別層級屬性。</span><span class="sxs-lookup"><span data-stu-id="9620a-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="9620a-124">下列程式碼範例示範如何使用 `LogEntry` 類別。</span><span class="sxs-lookup"><span data-stu-id="9620a-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="9620a-125">這個範例也會顯示 `LogEntry` 類型的 <xref:System.ComponentModel.TypeConverter> 的執行，稱為 `LogEntryTypeConverter`。</span><span class="sxs-lookup"><span data-stu-id="9620a-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="9620a-126">成員層級屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-126">Member-level Attributes</span></span>  
 <span data-ttu-id="9620a-127">某些屬性會在成員層級套用。</span><span class="sxs-lookup"><span data-stu-id="9620a-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="9620a-128">下列程式碼範例顯示一些通常會套用至 Windows Forms 控制項屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="9620a-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="9620a-129">AmbientValue 屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="9620a-130">下列範例示範 <xref:System.ComponentModel.AmbientValueAttribute>，並顯示支援其與設計環境互動的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9620a-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="9620a-131">此互動稱為「*環境*」。</span><span class="sxs-lookup"><span data-stu-id="9620a-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="9620a-132">資料系結屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-132">Databinding Attributes</span></span>  
 <span data-ttu-id="9620a-133">下列範例示範複雜資料系結的執行。</span><span class="sxs-lookup"><span data-stu-id="9620a-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="9620a-134">先前所示的類別層級 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>會指定用於資料系結的 `DataSource` 和 `DataMember` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9620a-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="9620a-135"><xref:System.ComponentModel.AttributeProviderAttribute> 指定 `DataSource` 屬性將系結的類型。</span><span class="sxs-lookup"><span data-stu-id="9620a-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9620a-136">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9620a-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="9620a-137">裝載 `AttributesDemoControl` 的表單需要 `AttributesDemoControl` 元件的參考，才能建立。</span><span class="sxs-lookup"><span data-stu-id="9620a-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9620a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9620a-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="9620a-139">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="9620a-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9620a-140">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="9620a-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="9620a-141">[如何：使用 Designerserializationvisibilityattribute 序列化序列化標準類型的集合](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9620a-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
