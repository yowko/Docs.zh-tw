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
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>如何：在 Windows Form 控制項中套用屬性
若要開發與設計環境正確互動並在執行時間正確執行的元件和控制項，您需要將屬性正確地套用至類別和成員。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何在自訂控制項上使用多個屬性。 此控制項會示範簡單的記錄功能。 當控制項系結至資料來源時，它會在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料來源所傳送的值。 如果值超過 `Threshold` 屬性所指定的值，就會引發 `ThresholdExceeded` 事件。  
  
 `AttributesDemoControl` 會記錄具有 `LogEntry` 類別的值。 `LogEntry` 類別是樣板類別，這表示它會在其所記錄的類型上進行參數化。 例如，如果 `AttributesDemoControl` 是記錄 `float`類型的值，則每個 `LogEntry` 實例都會宣告並使用，如下所示。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> 因為 `LogEntry` 是由任意型別參數化，所以它必須使用反映來指令引數型別。 若要讓 [臨界值] 功能正常執行，參數類型 `T` 必須實 <xref:System.IComparable> 介面。  
  
 裝載 `AttributesDemoControl` 的表單會定期查詢效能計數器。 每個值都封裝在適當類型的 `LogEntry` 中，並加入表單的 <xref:System.Windows.Forms.BindingSource>中。 `AttributesDemoControl` 會透過其資料系結接收值，並在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示值。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 第一個程式碼範例是 `AttributesDemoControl` 的執行。 第二個程式碼範例示範使用 `AttributesDemoControl`的表單。  
  
## <a name="class-level-attributes"></a>類別層級屬性  
 某些屬性會在類別層級套用。 下列程式碼範例顯示常用於 Windows Forms 控制項的屬性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 屬性  
 <xref:System.ComponentModel.TypeConverterAttribute> 是另一個常用的類別層級屬性。 下列程式碼範例示範如何使用 `LogEntry` 類別。 這個範例也會顯示 `LogEntry` 類型的 <xref:System.ComponentModel.TypeConverter> 的執行，稱為 `LogEntryTypeConverter`。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>成員層級屬性  
 某些屬性會在成員層級套用。 下列程式碼範例顯示一些通常會套用至 Windows Forms 控制項屬性的屬性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 屬性  
 下列範例示範 <xref:System.ComponentModel.AmbientValueAttribute>，並顯示支援其與設計環境互動的程式碼。 此互動稱為「*環境*」。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>資料系結屬性  
 下列範例示範複雜資料系結的執行。 先前所示的類別層級 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>會指定用於資料系結的 `DataSource` 和 `DataMember` 屬性。 <xref:System.ComponentModel.AttributeProviderAttribute> 指定 `DataSource` 屬性將系結的類型。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 裝載 `AttributesDemoControl` 的表單需要 `AttributesDemoControl` 元件的參考，才能建立。  
  
## <a name="see-also"></a>請參閱

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
- [Windows Forms 控制項中的屬性](attributes-in-windows-forms-controls.md)
- [如何：使用 Designerserializationvisibilityattribute 序列化序列化標準類型的集合](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
