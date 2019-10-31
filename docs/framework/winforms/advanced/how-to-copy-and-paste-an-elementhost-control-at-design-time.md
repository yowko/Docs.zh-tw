---
title: 如何：在設計階段複製和貼上 ElementHost 控制項
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
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197473"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>如何：複製和貼上 ElementHost 控制項

此程式說明如何在 Visual Studio 中複製 Windows Form 上的 Windows Presentation Foundation （WPF）控制項。

1. 在 Visual Studio 中，將新的 WPF <xref:System.Windows.Controls.UserControl> 加入至 Windows Forms 專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。

2. 在 [**屬性**] 視窗中，將 `UserControl1` 的 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。

3. 將 [<xref:System.Windows.Controls.Control.Background%2A>] 屬性的值設定為 [**藍色**]。

4. 建置專案。

5. 在 Windows Form 設計工具中開啟 `Form1`。

6. 從 [**工具箱**] 中，將 `UserControl1` 的實例拖曳至表單上。

   `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。

7. 選取 `elementHost1` 後，請按**Ctrl**+**C** ，將它複製到剪貼簿。

8. 按**Ctrl**+**V** ，將複製的控制項貼入表單上。

   會在表單上建立名為 `elementHost2` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
