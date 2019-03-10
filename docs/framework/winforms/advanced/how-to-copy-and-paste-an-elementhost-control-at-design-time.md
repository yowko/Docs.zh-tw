---
title: HOW TO：複製並貼上 ElementHost 控制項在設計階段
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 203a01ef82554bf4104f3000c0821cceeafac9f7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710416"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>HOW TO：複製並貼上 ElementHost 控制項在設計階段
此程序會示範如何複製 Windows Form 上的 Windows Presentation Foundation (WPF) 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>複製並貼上 ElementHost 控制項在設計階段  
  
1.  將新的 WPF<xref:System.Windows.Controls.UserControl>至您的 Windows Forms 專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在**屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>的屬性`UserControl1`至`200`。  
  
3.  將 <xref:System.Windows.Controls.Control.Background%2A> 屬性值設定為 `Blue`。  
  
4.  建置專案。  
  
5.  在 Windows Form 設計工具中開啟 `Form1`。  
  
6.  從**工具箱**，將拖曳的執行個體`UserControl1`拖曳至表單。  
  
     
  `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
7.  在選取 `elementHost1` 時，按 CTRL+C 將其複製到剪貼簿。  
  
8.  按下 CTRL + V 鍵貼上複製的控制項拖曳至表單。  
  
     新<xref:System.Windows.Forms.Integration.ElementHost>控制項，名為`elementHost2`建立表單上。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移轉和互通性](../../wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
