---
title: "逐步解說：在設計階段指派 Windows Form 的 WPF 內容 | Microsoft Docs"
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
  - "ElementHost 控制項, 在設計階段指派 WPF 內容"
  - "互通性 [WPF]"
  - "Windows Form, 內容指派"
  - "WPF 內容 [Windows Form], 在設計階段時指派"
  - "WPF 使用者控制項, 在 Windows Form 中裝載"
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 逐步解說：在設計階段指派 Windows Form 的 WPF 內容
本逐步解說示範如何選取要在表單上顯示的 Windows Presentation Foundation \(WPF\) 控制項類型。  您可以選取包含在專案中的任何 WPF 控制項類型。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立專案。  
  
-   建立 WPF 控制項類型。  
  
-   選取 WPF 控制項。  
  
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
  
-   在 Visual Basic 或 Visual C\# 中，建立名為 `SelectingWpfContent` 的新 Windows Form 應用程式專案。  
  
## 建立 WPF 控制項類型  
 當您將 WPF 控制項類型加入專案之後，即可在不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中裝載這些類型。  
  
#### 建立 WPF 控制項類型  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。  使用控制項類型的預設名稱 `UserControl1.xaml`。  如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在 \[設計\] 檢視中，確定已選取 `UserControl1`。  如需詳細資訊，請參閱[HOW TO：在設計介面上選取並移動項目](http://msdn.microsoft.com/zh-tw/54cb70b6-b35b-46e4-a0cc-65189399c474)。  
  
3.  在 \[屬性\] 視窗中，將 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的值設定為 `200`。  
  
4.  將 <xref:System.Windows.Controls.TextBox?displayProperty=fullName> 控制項加入 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 \[裝載的內容\]。  
  
5.  將第二個 WPF <xref:System.Windows.Controls.UserControl> 加入專案。  使用控制項類型的預設名稱 `UserControl2.xaml`。  
  
6.  在 \[屬性\] 視窗中，將 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的值設定為 `200`。  
  
7.  將 <xref:System.Windows.Controls.TextBox?displayProperty=fullName> 控制項加入 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 \[裝載的內容 2\]。  
  
 **注意**：一般而言，您應該裝載更複雜的 WPF 內容。  <xref:System.Windows.Controls.TextBox?displayProperty=fullName> 控制項在此僅供說明用途使用。  
  
1.  建置專案。  
  
## 選取 WPF 控制項  
 您可以對已裝載內容的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，指派不同的 WPF 內容。  
  
#### 選取 WPF 控制項  
  
1.  在 Windows Form 設計工具中開啟 `Form1`。  
  
2.  在 \[工具箱\] 中，按兩下 `UserControl1`，在表單上建立 `UserControl1` 的執行個體。  
  
     `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
3.  在 `elementHost1` 的智慧標籤面板中，開啟 \[選擇裝載內容\] 下拉式清單。  
  
4.  從下拉式清單方塊中選取 \[UserControl2\]。  
  
     `elementHost1` 控制項現在會裝載 `UserControl2` 類型的執行個體。  
  
5.  在 \[屬性\] 視窗中，確認將 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> 屬性設定為 **UserControl2**。  
  
6.  從 \[工具箱\] 的 \[WPF 互通性\] 群組，將 <xref:System.Windows.Forms.Integration.ElementHost> 控制項拖曳到表單上。  
  
     新控制項的預設名稱為 `elementHost2`。  
  
7.  在 `elementHost2` 的智慧標籤面板中，開啟 \[選擇裝載內容\] 下拉式清單。  
  
8.  從下拉式清單中選取 \[UserControl1\]。  
  
9. `elementHost2` 控制項現在會裝載 `UserControl1` 類型的執行個體。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)