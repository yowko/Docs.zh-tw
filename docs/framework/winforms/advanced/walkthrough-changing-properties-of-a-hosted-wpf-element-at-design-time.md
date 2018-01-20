---
title: "逐步解說：在設計階段變更已裝載之 WPF 項目的屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b80ee0c74da7371ac8f7a16d3430b5b753059d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>逐步解說：在設計階段變更已裝載之 WPF 項目的屬性
本逐步解說示範如何變更 Windows Form 上裝載的 Windows Presentation Foundation (WPF) 控制項的屬性值。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立專案。  
  
-   建立 WPF 控制項。  
  
-   在 Windows Form 上裝載 WPF 控制項。  
  
-   使用 WPF Designer for Visual Studio 來變更屬性值。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`WpfHost`。  
  
## <a name="creating-the-wpf-control"></a>建立 WPF 控制項  
 在將 WPF 控制項加入專案後，即可在表單上予以排列。  
  
#### <a name="to-create-wpf-controls"></a>建立 WPF 控制項  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說： 建立的新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在**屬性**視窗中，設定的值<xref:System.Windows.Controls.Control.Background%2A>屬性`Blue`。  
  
3.  建置專案。  
  
## <a name="changing-property-values-on-the-wpf-control"></a>變更 WPF 控制項的屬性值  
 <xref:System.Windows.Forms.Integration.ElementHost> 智慧標籤可藉由使用 WPF 設計工具，輕鬆地變更裝載 WPF 內容的屬性。  
  
#### <a name="to-host-a-wpf-control"></a>裝載 WPF 控制項  
  
1.  在 Windows Form 設計工具中開啟 `Form1`。  
  
2.  在**工具箱**，請在**WPF 使用者控制項**索引標籤上，按兩下`UserControl1`建立的執行個體`UserControl1`表單上。  
  
     `UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
3.  在**ElementHost 工作**智慧標籤面板中，選取**編輯裝載內容**。  
  
     UserControl1.xaml 檔案會在 WPF 設計工具中開啟。  
  
4.  在**屬性**視窗中，設定的值<xref:System.Windows.Controls.Control.Background%2A>屬性`Red`。  
  
5.  重建專案。  
  
6.  在 Windows Form 設計工具中開啟 `Form1`。  
  
     `UserControl1` 的執行個體具有紅色背景。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [操作說明：在設計階段將控制項對齊表單邊緣](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [逐步解說：使用對齊線排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
