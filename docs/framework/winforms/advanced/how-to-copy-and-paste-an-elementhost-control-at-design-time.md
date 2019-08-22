---
title: HOW TO：在設計階段複製和貼上 ElementHost 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666172"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>HOW TO：複製並貼上 ElementHost 控制項

此程式說明如何在 Visual Studio 中複製 Windows Form 上的 Windows Presentation Foundation (WPF) 控制項。

1. 在 Visual Studio 中, 將新的<xref:System.Windows.Controls.UserControl> WPF 加入 Windows Forms 專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)于 Windows Forms 上建立新的 WPF 內容。

2. 在 [**屬性**] 視窗中<xref:System.Windows.FrameworkElement.Width%2A> , 將的和<xref:System.Windows.FrameworkElement.Height%2A>屬性`UserControl1`的值設定為**200**。

3. 將<xref:System.Windows.Controls.Control.Background%2A>屬性的值設定為**Blue**。

4. 建置專案。

5. 在 Windows Form 設計工具中開啟 `Form1`。

6. 將的實例`UserControl1`從 [工具箱] 拖曳到表單上。

   `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

7. 選取`elementHost1`時, 請按**Ctrl** + **C**將它複製到剪貼簿。

8. 按**Ctrl** + **V** , 將複製的控制項貼入表單上。

   會在<xref:System.Windows.Forms.Integration.ElementHost>表單`elementHost2`上建立名為的新控制項。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
