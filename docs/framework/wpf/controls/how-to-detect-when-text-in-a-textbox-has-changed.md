---
title: 作法：偵測 TextBox 中的文字何時變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855615"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>作法：偵測 TextBox 中的文字何時變更

這個範例示範當<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> <xref:System.Windows.Controls.TextBox>控制項中的文字變更時，使用事件來執行方法的一種方式。

在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含您想要<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法。<xref:System.Windows.Controls.TextBox>  這個方法的簽章必須與<xref:System.Windows.Controls.TextChangedEventHandler>委派所預期的簽章相符。

每當使用者或以程式設計方式變更<xref:System.Windows.Controls.TextBox>控制項的內容時，就會呼叫事件處理常式。

> [!NOTE]
> 這個事件會在建立<xref:System.Windows.Controls.TextBox>控制項時引發，而且一開始會以文字填入。

## <a name="example"></a>範例

在定義控制項的中，使用符合事件<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>處理常式方法名稱的值來指定屬性。 <xref:System.Windows.Controls.TextBox> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>範例

在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含您想要<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法。<xref:System.Windows.Controls.TextBox>  這個方法的簽章必須與<xref:System.Windows.Controls.TextChangedEventHandler>委派所預期的簽章相符。

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

每當使用者或以程式設計方式變更<xref:System.Windows.Controls.TextBox>控制項的內容時，就會呼叫事件處理常式。

> [!NOTE]
> 這個事件會在建立<xref:System.Windows.Controls.TextBox>控制項時引發，而且一開始會以文字填入。

註解

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
