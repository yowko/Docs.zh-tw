---
title: "各種自訂控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "複合控制項"
  - "控制項 [Windows Form], 複合"
  - "控制項 [Windows Form], 延伸"
  - "控制項 [Windows Form], 類型"
  - "控制項 [Windows Form], 使用者控制項"
  - "自訂控制項 [Windows Form]"
  - "擴充的控制項"
  - "使用者控制項 [Windows Form]"
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 各種自訂控制項
藉由 .NET Framework，可以開發及實作新的控制項。  您可以透過繼承 \(Inheritance\) 擴充熟悉的使用者控制項以及現有控制項的功能，  也可以撰寫自行執行繪製作業的自訂控制項。  
  
 決定要建立哪種類型的控制項，可能會令人感到困惑。  這個主題強調您可繼承的各種控制項之間的差異，並提供您如何為專案選擇特定控制項的詳細資訊。  
  
> [!NOTE]
>  如需撰寫使用在 Web Form 上的控制項的詳細資訊，請參閱[Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)。  
  
## 基底控制項類別  
 <xref:System.Windows.Forms.Control> 類別是 Windows Form 控制項的基底類別。  它提供在 Windows Form 應用程式中進行視覺顯示所需的基礎結構。  
  
 <xref:System.Windows.Forms.Control> 類別執行下列工作，在 Windows Form 應用程式中提供視覺顯示：  
  
-   公開視窗控制代碼  
  
-   管理訊息路由  
  
-   提供滑鼠與鍵盤事件，及許多其他使用者介面事件  
  
-   提供進階的配置功能  
  
-   包含許多視覺顯示特定的屬性，例如 <xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Height%2A> 和 <xref:System.Windows.Forms.Control.Width%2A>。  
  
-   提供 Windows Form 控制項要做為 Microsoft® ActiveX® 控制項所需要的安全性和執行緒支援  
  
 因為基底類別提供如此大量的基礎結構，開發您自己的 Windows Form 控制項變得相當容易。  
  
## 控制項的種類  
 Windows Form 支援三種使用者定義的控制項：「*複合*」、「*擴充*」和「*自訂*」。  下列章節會說明每一種控制項，並針對要在專案中選澤使用何種控制項提供了建議。  
  
### 複合控制項  
 複合控制項是封裝在通用容器 \(Container\) 中的 Windows Form 控制項的集合。  這種控制項有時稱為「*使用者控制項*」。  被收納的控制項稱為「*構成控制項*」。  
  
 複合控制項保留與每個被收納的 Windows Form 控制項關聯的所有繼承功能，且可讓您選擇性地公開及繫結其屬性。  複合控制項也提供了許多預設的鍵盤處理功能，使您不需要耗費額外的心力在開發工作上。  
  
 例如，可以建置複合控制項，以顯示資料庫的客戶地址資料。  這個控制項可能包含顯示資料庫欄位的 <xref:System.Windows.Forms.DataGridView> 控制項、處理繫結至資料來源的 <xref:System.Windows.Forms.BindingSource>，以及在資料錄之間移動的 <xref:System.Windows.Forms.BindingNavigator> 控制項。  您可以選擇性地公開資料繫結屬性，且能夠在不同的應用程式之間封裝並重複使用整個控制項。  如需這種複合控制項的詳細資訊，請參閱 [如何：在 Windows Form 控制項中套用屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)。  
  
 若要撰寫複合控制項，請衍生自 <xref:System.Windows.Forms.UserControl> 類別。  基底類別 <xref:System.Windows.Forms.UserControl> 提供子控制項的鍵盤路由，並讓子控制項能夠當做群組使用。  如需詳細資訊，請參閱[開發複合 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)。  
  
 **建議**  
  
 如果發生下列情況，請繼承 <xref:System.Windows.Forms.UserControl> 類別：  
  
-   您要將多個 Windows Form 控制項的功能結合至單一可重複使用的單位。  
  
### 擴充控制項  
 您可以從任何現有的 Windows Form 控制項衍生出繼承控制項。  透過這個方法，可以保留 Windows Form 控制項的所有繼承功能，然後藉由加入自訂屬性、方法或其他功能來擴充該功能。  您可以使用這個選項來覆寫基底控制項的繪製邏輯，然後藉由變更外觀來擴充它的使用者介面。  
  
 例如，您可以建立衍生自 <xref:System.Windows.Forms.Button> 控制項的控制項，追蹤使用者點選該控制項的次數。  
  
 在部分控制項中，也可以藉由覆寫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，將自訂外觀加入控制項的圖形化使用者介面。  對於追蹤點選次數的擴充按鈕，您可以覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法以呼叫 <xref:System.Windows.Forms.Control.OnPaint%2A> 的基底實作，然後在 <xref:System.Windows.Forms.Button> 控制項工作區 \(Client Area\) 的其中一個角落中，繪製點選計數。  
  
 **建議**  
  
 如果發生下列情況，請繼承 Windows Form 控制項：  
  
-   您需要的大部分功能與現有的 Windows Form 控制項相同。  
  
-   您不需要自訂的圖形化使用者介面，或者希望針對現有的控制項設計新的圖形化使用者介面  
  
### 自訂控制項  
 建立控制項的另一種方式，是藉由繼承自 <xref:System.Windows.Forms.Control> 來建立控制項，這種方式幾乎是從頭建置控制項。  <xref:System.Windows.Forms.Control> 類別提供控制項所需的所有基本功能 \(包括滑鼠和鍵盤處理事件\)，但不提供控制項特定的功能或圖形介面。  
  
 藉由繼承 <xref:System.Windows.Forms.Control> 類別以建立控制項，比繼承 <xref:System.Windows.Forms.UserControl> 或現有的 Windows Form 控制項更費心力。  因為您擁有許多實作的空間，所以產生的控制項可擁有比複合或擴充控制項還要大的彈性，並且可以量身訂做以符合真正的需求。  
  
 若要實作自訂控制項，您必須為控制項的 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件撰寫程式碼，以及撰寫所需的任何功能特定的程式碼。  您也可以覆寫 <xref:System.Windows.Forms.Control.WndProc%2A> 方法，並直接處理 Windows 訊息。  這是建立控制項最有力的方法，但是要有效使用這項技術，您需要熟悉 Microsoft Win32® API。  
  
 複製類比時鐘的外觀和行為的時鐘控制項，是自訂控制項的一個範例。  在此控制項中叫用 \(Invoke\) 了自訂繪製，使時鐘的指針依據內部 <xref:System.Windows.Forms.Timer> 元件的 <xref:System.Windows.Forms.Timer.Tick> 事件來移動。  如需詳細資訊，請參閱 [如何：開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)。  
  
 **建議**  
  
 如果發生下列情況，請繼承 <xref:System.Windows.Forms.Control> 類別：  
  
-   您要提供您控制項的自訂圖形表示。  
  
-   您需要實作無法從標準控制項取得的自訂功能。  
  
### ActiveX 控制項  
 雖然 Windows Form 基礎結構已經最佳化以裝載 \(Host\) Windows Form 控制項，您仍然可以使用 ActiveX 控制項。  Visual Studio 中會支援這項工作。  如需詳細資訊，請參閱 [如何：將 ActiveX 控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)。  
  
### 無視窗控制項  
 Microsoft Visual Basic® 6.0 和 ActiveX 技術支援「*無視窗*」控制項。  Windows Form 不支援無視窗控制項。  
  
## 自訂設計經驗  
 如果需要實作自訂的設計階段經驗，可以撰寫自己的設計工具。  針對複合控制項，請從 <xref:System.Windows.Forms.Design.ParentControlDesigner> 或 <xref:System.Windows.Forms.Design.DocumentDesigner> 類別衍生您的自訂設計工具類別。  針對擴充及自訂控制項，請從 <xref:System.Windows.Forms.Design.ControlDesigner> 類別衍生您的自訂設計工具類別。  
  
 使用 <xref:System.ComponentModel.DesignerAttribute> 將您的控制項與設計工具相關聯。  如需詳細資訊，請參閱[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)和 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)。  
  
## 請參閱  
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [如何：開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [開發複合 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)