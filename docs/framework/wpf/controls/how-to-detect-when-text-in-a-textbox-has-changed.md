---
title: 如何：偵測 TextBox 中的文字何時變更
description: 瞭解當 TextBox 控制項中的文字在 Windows Presentation Foundation 應用程式中變更時，如何使用 TextChanged 事件來執行方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166219"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>如何：偵測 TextBox 中的文字何時變更

這個範例示範 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 當控制項中的文字變更時，使用事件來執行方法的一種方式 <xref:System.Windows.Controls.TextBox> 。

在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含 <xref:System.Windows.Controls.TextBox> 您想要監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。  這個方法的簽章必須與委派所預期的簽章相符 <xref:System.Windows.Controls.TextChangedEventHandler> 。

每當 <xref:System.Windows.Controls.TextBox> 使用者或以程式設計方式變更控制項的內容時，就會呼叫事件處理常式。

> [!NOTE]
> 這個事件 <xref:System.Windows.Controls.TextBox> 會在建立控制項時引發，而且一開始會以文字填入。

## <a name="example"></a>範例

在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義控制項的中 <xref:System.Windows.Controls.TextBox> ， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 使用符合事件處理常式方法名稱的值來指定屬性。

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>範例

在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 包含 <xref:System.Windows.Controls.TextBox> 您想要監視變更之控制項的程式碼後置類別中，插入每當引發事件時要呼叫的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。  這個方法的簽章必須與委派所預期的簽章相符 <xref:System.Windows.Controls.TextChangedEventHandler> 。

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

每當 <xref:System.Windows.Controls.TextBox> 使用者或以程式設計方式變更控制項的內容時，就會呼叫事件處理常式。

> [!NOTE]
> 這個事件 <xref:System.Windows.Controls.TextBox> 會在建立控制項時引發，而且一開始會以文字填入。

註解

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
