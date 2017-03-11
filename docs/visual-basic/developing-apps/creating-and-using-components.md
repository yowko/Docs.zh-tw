---
title: "Creating and Using Components in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "components [Visual Basic]"
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Creating and Using Components in Visual Basic
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

「*元件*」\(Component\) 是實作 <xref:System.ComponentModel.IComponent?displayProperty=fullName> 介面的類別，或是從實作 <xref:System.ComponentModel.IComponent> 之類別直接或間接衍生的類別。  [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort-md.md)] 元件是可重複使用的物件，能與其他物件互動，並提供對外部資源的控制和設計階段的支援。  
  
 元件的其中一項重要特色是使用者可以設計元件，這表示本身為元件的類別，可以用於 [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)] 整合式開發環境。  元件可以加入至 \[工具箱\]、拖放到表單上，以及在設計介面上操作。  請注意，元件的基底設計階段支援是內建於 [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort-md.md)]，元件開發人員不必執行額外的工作，就能利用基底設計階段的功能。  
  
 「*控制項*」\(Control\) 與元件類似，都是可以設計的。  不過，控制項會提供使用者介面，元件則不提供。  控制項必須衍生自下列其中一個基底控制項類別：<xref:System.Windows.Forms.Control> 或 <xref:System.Web.UI.Control>。  
  
## 建立元件的時機  
 如果您的類別會用在設計介面上 \(例如 Windows Form 或 Web Form 設計工具\)，但是卻沒有使用者介面，則它必須是元件並會實作 <xref:System.ComponentModel.IComponent>，或是從實作 <xref:System.ComponentModel.IComponent> 的類別直接或間接衍生的。  
  
 <xref:System.ComponentModel.Component> 和 <xref:System.ComponentModel.MarshalByValueComponent> 類別都是 <xref:System.ComponentModel.IComponent> 介面的基底實作。  這些類別的主要差異在於，<xref:System.ComponentModel.Component> 類別是以傳址 \(By Reference\) 方式封送處理，而 <xref:System.ComponentModel.IComponent> 則是以傳值 \(By Value\) 方式封送處理。  下列清單會為實作人員提供較廣泛的方針。  
  
-   如果元件必須以傳址方式封送處理，請從 <xref:System.ComponentModel.Component> 衍生。  
  
-   如果元件必須以傳值方式封送處理，則從 <xref:System.ComponentModel.MarshalByValueComponent> 衍生。  
  
-   如果元件因單一繼承 \(Inheritance\) 問題，而無法從其中一個基底實作衍生，則請實作 <xref:System.ComponentModel.IComponent>。  
  
 如需設計階段支援的詳細資訊，請參閱 [元件的設計階段屬性](../Topic/Design-Time%20Attributes%20for%20Components.md)和[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)。  
  
## 元件類別  
 <xref:System.ComponentModel> 命名空間提供類別，用於實作元件和控制項的執行階段和設計階段行為。  這個命名空間會包含基底類別 \(Base Class\) 和介面，用於實作屬性 \(Attribute\) 和型別轉換子 \(Type Converter\)、繫結至資料來源，以及授權元件。  
  
 核心元件類別包括：  
  
-   <xref:System.ComponentModel.Component>.  <xref:System.ComponentModel.IComponent> 介面的基底實作。  此類別允許在應用程式之間共用物件。  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>.  <xref:System.ComponentModel.IComponent> 介面的基底實作。  
  
-   <xref:System.ComponentModel.Container>.  <xref:System.ComponentModel.IContainer> 介面的基底實作。  此類別會封裝零或多個元件。  
  
 用於元件授權的類別包括：  
  
-   <xref:System.ComponentModel.License>.  所有授權的抽象基底類別。  授與元件的某個特定執行個體 \(Instance\) 一個授權。  
  
-   <xref:System.ComponentModel.LicenseManager>.  提供屬性和方法，以加入授權至元件和管理 <xref:System.ComponentModel.LicenseProvider>。  
  
-   <xref:System.ComponentModel.LicenseProvider>.  實作授權提供者的抽象基底類別。  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>.  指定要與類別一起使用的 <xref:System.ComponentModel.LicenseProvider> 類別。  
  
 描述和保存元件的常用類別：  
  
-   <xref:System.ComponentModel.TypeDescriptor>.  提供元件特性的相關資訊，例如其屬性 \(Attribute\)、屬性 \(Property\) 和事件。  
  
-   <xref:System.ComponentModel.EventDescriptor>.  提供事件的相關資訊。  
  
-   <xref:System.ComponentModel.PropertyDescriptor>.  提供有關屬性的資訊。  
  
## 相關章節  
 [類別、元件和控制項的比較](../Topic/Class%20vs.%20Component%20vs.%20Control.md)  
 定義「*元件*」\(Component\) 和「*控制項*」\(Control\)，並討論這兩者和類別之間的差異。  
  
 [元件撰寫](../Topic/Component%20Authoring.md)  
 開始使用元件的資料表。  
  
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)  
 連結一些主題，這些主題會提供元件程式設計的逐步指示。  
  
 [元件類別](../Topic/Component%20Classes.md)  
 說明類別如何成為元件、公開元件功能的方法、控制元件存取以及控制如何建立元件執行個體。  
  
 [控制項和元件撰寫疑難排解](../Topic/Troubleshooting%20Control%20and%20Component%20Authoring.md)  
 說明如何修復常見問題。  
  
## 請參閱  
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)   
 [How to: Extend the Appearance and Behavior of Controls in Design Mode](../Topic/How%20to:%20Extend%20the%20Appearance%20and%20Behavior%20of%20Controls%20in%20Design%20Mode.md)   
 [How to: Perform Custom Initialization for Controls in Design Mode](../Topic/How%20to:%20Perform%20Custom%20Initialization%20for%20Controls%20in%20Design%20Mode.md)