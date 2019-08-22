---
title: 逐步解說：在設計階段建立 Windows Forms 的新 WPF 內容
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3fb6e42270cc0a530646b656470ec99fcfc7f1f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666239"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容

本文說明如何建立 Windows Presentation Foundation (WPF) 控制項, 以便在您的 Windows Forms 架構應用程式中使用。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-project"></a>建立專案

第一個步驟是建立 Windows Form 專案。 開啟 Visual Studio, 並在 Visual Basic 或視覺效果C#中建立名為`HostingWpf`的新**Windows Forms 應用程式 (.NET Framework)** 專案。

> [!NOTE]
> 裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。

## <a name="create-a-new-wpf-control"></a>建立新的 WPF 控制項

建立新的 WPF 控制項並將其加入專案中，就像是將其他任何項目加入專案中一樣容易。 Windows Form 設計工具適用于特定類型的控制項, 稱為*複合控制項*或*使用者控制項*。 如需 WPF 使用者控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.UserControl>。

> [!NOTE]
> WPF 的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 類型不同於 Windows Form 所提供的使用者控制項類型 (又稱為 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>)。

若要建立新的 WPF 控制項:

1. 在**方案總管**中, 將新的**WPF 使用者控制項程式庫 (.NET Framework)** 專案加入至方案。 使用控制項程式庫的預設名稱 `WpfControlLibrary1`。 預設控制項名稱為 `UserControl1.xaml`。

   加入新控制項的效果如下:

   - 會加入 UserControl1.xaml 檔案。

   - 已新增檔案 UserControl1.xaml.cs (或 UserControl1)。 這個檔案包含事件處理常式和其他實作的程式碼後置。

   - 會加入 WPF 組件的參考。

   - [檔案 UserControl1] 會在 WPF 設計工具中開啟 Visual Studio。

2. 在 [設計] 檢視中，確定已選取 `UserControl1`。

3. 在 [**屬性**] 視窗中, 將<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性的值設定為**200**。

4. 將<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>控制項從 [**工具箱**] 拖曳到設計介面上。

5. 在 [**屬性**] 視窗中, 將<xref:System.Windows.Controls.TextBox.Text%2A>屬性的值設定為 [**主控內容**]。

   > [!NOTE]
   > 一般而言，您應該裝載更複雜的 WPF 內容。 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。

6. 建置專案。

## <a name="add-a-wpf-control-to-a-windows-form"></a>將 WPF 控制項加入至 Windows Form

您的新 WPF 控制項已經準備好在表單上使用。 Windows Forms 使用<xref:System.Windows.Forms.Integration.ElementHost>控制項來裝載 WPF 內容。

若要將 WPF 控制項加入至 Windows Form:

1. 在 Windows Form 設計工具中開啟 `Form1`。

2. 在 [**工具箱**] 中, 尋找標示為 [ **WPFUserControlLibrary WPF 使用者控制項**] 的索引標籤。

3. 將 `UserControl1` 的執行個體拖曳到表單上。

    - <xref:System.Windows.Forms.Integration.ElementHost> 控制項會在表單上自動建立，以裝載 WPF 控制項。

    - `elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>控制項的名稱為, 而在 [屬性] 視窗中, 您可以看到其屬性設定為 UserControl1。 <xref:System.Windows.Forms.Integration.ElementHost>

    - WPF 組件的參考會加入專案中。

    - `elementHost1` 控制項具有智慧標籤面板，這個面板會顯示可用的裝載選項。

4. 在 [ **ElementHost Tasks** ] 智慧標籤面板中, 選取 [停**駐于父容器中**]。

5. 按 **F5** 鍵建置並執行應用程式。

## <a name="next-steps"></a>後續步驟

Windows Form 和 WPF 是不同的技術，不過可以藉由設計密切地相互操作。 若要在您的應用程式中提供更豐富的外觀和行為, 請嘗試下列步驟:

- 將 Windows Form 控制項裝載到 WPF 頁面中。 如需詳細資訊，請參閱[逐步解說：在 WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)中裝載 Windows Forms 控制項。

- 將 Windows Form 視覺化樣式套用至 WPF 內容。 如需詳細資訊，請參閱[如何：在混合式應用程式](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)中啟用視覺化樣式。

- 變更 WPF 內容的樣式。 如需詳細資訊，請參閱[逐步解說：設定 WPF 內容](walkthrough-styling-wpf-content.md)的樣式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
