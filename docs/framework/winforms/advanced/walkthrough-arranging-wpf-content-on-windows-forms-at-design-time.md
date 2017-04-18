---
title: "逐步解說：在設計階段排列 Windows Form 的 WPF 內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "互通性 [WPF]"
  - "Windows Form, 錨定和停駐 WPF 內容"
  - "Windows Form, 在設計階段排列 WPF 內容"
  - "WPF 內容 [Windows Form], 在設計階段時排列"
  - "WPF 內容, 在 Windows Form 中裝載"
  - "WPF 使用者控制項 [Windows Form], 裝載在配置面板中"
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 逐步解說：在設計階段排列 Windows Form 的 WPF 內容
本逐步解說示範如何使用 Windows Form 的配置功能 \(例如錨定和對齊線\)，來排列 Windows Presentation Foundation \(WPF\) 控制項。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立專案。  
  
-   建立 WPF 控制項。  
  
-   將 WPF 控制項裝載到配置面板中。  
  
-   使用對齊線來對齊 WPF 控制項。  
  
-   錨定和停駐 WPF 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## 建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C\# 和 Visual Basic 專案。  
  
#### 若要建立專案  
  
-   在 Visual Basic 或 Visual C\# 中，建立名為 `ArrangeElementHost` 的新 Windows Form 應用程式專案。  
  
## 建立 WPF 控制項  
 在將 WPF 控制項加入專案後，即可在表單上予以排列。  
  
#### 建立 WPF 控制項  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。  使用控制項類型的預設名稱 `UserControl1.xaml`。  如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在 \[設計\] 檢視中，確定已選取 `UserControl1`。  如需詳細資訊，請參閱[HOW TO：在設計介面上選取並移動項目](http://msdn.microsoft.com/zh-tw/54cb70b6-b35b-46e4-a0cc-65189399c474)。  
  
3.  在 \[屬性\] 視窗中，將 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的值設定為 `200`。  
  
4.  將 <xref:System.Windows.Controls.Control.Background%2A> 屬性的值設定為 `Blue`。  
  
5.  建置專案。  
  
## 將 WPF 控制項裝載到配置面板中  
 您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。  
  
#### 將 WPF 控制項裝載到配置面板中  
  
1.  在 Windows Form 設計工具中開啟 `Form1`。  
  
2.  在 \[工具箱\] 中，將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳到表單上。  
  
3.  在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的智慧標籤面板上，選取 \[移除最後一個資料列\]。  
  
4.  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。  
  
5.  在 \[工具箱\] 中，按兩下 `UserControl1`，在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個儲存格中建立 `UserControl1` 的執行個體。  
  
     `UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
6.  在 \[工具箱\] 中，按兩下 `UserControl1`，在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第二個儲存格中建立另一個執行個體。  
  
7.  在 \[文件大綱\] 視窗中，選取 `tableLayoutPanel1`。  如需詳細資訊，請參閱[Document Outline Window](http://msdn.microsoft.com/zh-tw/9054f2bc-f6f8-4242-9fe0-be71089b12f8)。  
  
8.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Control.Padding%2A> 屬性的值設定為 `10, 10, 10, 10`。  
  
     兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。  
  
## 使用對齊線來對齊 WPF 控制項  
 對齊線可讓您輕鬆對齊表單上的控制項。  您也可以使用對齊線來對齊 WPF 控制項。  如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
#### 使用對齊線來對齊 WPF 控制項  
  
1.  將 `UserControl1` 的執行個體從 \[工具箱\] 拖曳到表單上，並將其放置到 <xref:System.Windows.Forms.TableLayoutPanel> 控制項下方的空間。  
  
     `UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
2.  使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。  
  
3.  使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。  
  
4.  將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。  
  
5.  在 \[屬性\] 視窗中，將 Margin 屬性的值設定為 `20, 20, 20, 20`。  
  
6.  將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。  中央對齊線現在表示邊界 20。  
  
7.  將 `elementHost3` 向右移，直到其左邊緣與 `elementHost1` 的左邊緣對齊為止。  
  
8.  變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。  
  
## 錨定和停駐 WPF 控制項  
 裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。  
  
#### 錨定和停駐 WPF 控制項  
  
1.  選取 `elementHost1`。  
  
2.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定為 **Top、Bottom、 Left、Right**。  
  
3.  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。  
  
     `elementHost1` 控制項會調整大小以填滿儲存格。  
  
4.  選取 `elementHost2`。  
  
5.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle>。  
  
     `elementHost2` 控制項會調整大小以填滿儲存格。  
  
6.  選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
7.  將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle>。  
  
8.  選取 `elementHost3`。  
  
9. 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle>。  
  
     `elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。  
  
10. 調整表單的大小。  
  
     這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。  
  
     如需詳細資訊，請參閱[如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [如何：在設計階段將控制項對齊表單邊緣](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)