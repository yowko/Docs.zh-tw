---
title: "如何：設定 Windows Form 面板的背景 | Microsoft Docs"
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
  - "背景色彩, Windows Form Panel 控制項"
  - "背景影像, Windows Form Panel 控制項"
  - "色彩, Windows Form Panel 控制項"
  - "Panel 控制項 [Windows Form], 背景"
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：設定 Windows Form 面板的背景
Windows Form <xref:System.Windows.Forms.Panel> 控制項可顯示背景色彩和背景影像。  <xref:System.Windows.Forms.Control.BackColor%2A> 屬性設定被收納的控制項 \(Contained Control\) 之背景色彩，如標籤 \(Label\) 和選項按鈕。  如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性未設定，則選取的 <xref:System.Windows.Forms.Control.BackColor%2A> 會填滿整個面板。  如果設定了 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性，則影像會顯示在被收納的控制項之後。  
  
### 若要以程式設計的方式來設定背景  
  
1.  設定面板的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性為 <xref:System.Drawing.Color?displayProperty=fullName> 型別的值。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  使用 <xref:System.Drawing.Image?displayProperty=fullName> 類別的 <xref:System.Drawing.Image.FromFile%2A> 方法，設定面板的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)