---
title: "使用視覺化樣式呈現控制項 | Microsoft Docs"
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
  - "專業外觀, 呈現 Windows Forms 控制項"
  - "佈景主題, Windows Forms 中的 XP 視覺化樣式"
  - "自訂控制項 [Windows Forms], 呈現"
  - "自訂控制項 [Windows Forms], 繪製"
  - "視覺化佈景主題, 呈現 Windows Forms 控制項"
  - "使用者控制項 [Windows Forms], 繪製"
  - "視覺化樣式, 呈現 Windows Forms 控制項"
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 使用視覺化樣式呈現控制項
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 會使用作業系統支援的視覺化樣式，來支援控制項和其他 Windows 使用者介面 \(UI\) 項目的呈現。 本主題說明在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中使用作業系統目前的視覺化樣式，來呈現控制項和其他 UI 項目的數種支援層級。  
  
## 呈現通用控制項的類別  
 呈現控制項是指繪製控制項的使用者介面。<xref:System.Windows.Forms?displayProperty=fullName> 命名空間提供的 <xref:System.Windows.Forms.ControlPaint> 類別可用來呈現一些通用的 Windows Forms 控制項。 不過，此類別會使用傳統的 Windows 樣式來繪製控制項，並導致在啟用視覺化樣式的應用程式中繪製自訂控制項時，很難保持一致的 UI 經驗。  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 包含 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中的類別，其可使用視覺化樣式呈現通用控制項的組件與狀態。 每個類別皆包括 `static` 方法，可在使用作業系統目前的視覺化樣式時，繪製控制項或特定狀態的控制項組件。  
  
 不論是否可以使用視覺化樣式，在這些類別中，有一些類別是專門設計來繪製相關的控制項。 如果啟用了視覺化樣式，則類別成員會使用視覺化樣式繪製相關控制項；如果停用了視覺化樣式，類別成員會以傳統的 Windows 樣式繪製控制項。 這些類別包括：  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 其他類別只能夠在視覺化樣式可用時，繪製相關的控制項，如果停用了視覺化樣式，類別成員便會擲回例外狀況。 這些類別包括：  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 如需使用這些類別繪製控制項的詳細資訊，請參閱 [如何：使用控制項呈現類別](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md)。  
  
## 視覺化樣式項目和呈現類別  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間所包含的類別可以用來繪製視覺化樣式所支援的任何控制項或 UI 項目，並取得相關的詳細資訊。 支援的控制項包括：在 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間中具有呈現類別的通用控制項 \(請參閱上一節\)，以及其他控制項 \(例如索引標籤控制項和 Rebar 控制項\)。 其他支援的 UI 項目包含 \[開始\] 功能表組件、工具列以及視窗的非工作區。  
  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間的主要類別是 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 和 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>。<xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 是基礎類別，可供識別視覺化樣式支援的任何控制項或使用者介面項目。 除了 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 本身以外，<xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間還包含許多具有 `static` 屬性的 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 巢狀類別，該屬性會為視覺化樣式支援的控制項、控制項組件或其他 UI 項目的每個狀態，傳回 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>。  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 提供相關方法，可供繪製作業系統目前的視覺化樣式所定義的每一個 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>，並取得其資訊。 系統可以擷取的項目資訊包括：其預設大小、背景類型和色彩定義。<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 包裝了 Windows Platform SDK 之 Windows Shell 部分的視覺化樣式 \(UxTheme\) API 功能。 如需詳細資訊，請參閱 MSDN Library \([http:\/\/msdn.microsoft.com\/library](http://msdn.microsoft.com/library/)\) 中 Platform SDK 部分的＜使用 Windows XP 視覺化樣式＞。  
  
 如需使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 和 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 的詳細資訊，請參閱 [如何：呈現視覺化樣式項目](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md)。  
  
## 啟用視覺化樣式  
 若要在為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版撰寫的應用程式中啟用視覺化樣式，程式設計人員必須包含應用程式資訊清單，以指定使用 ComCtl32.dll 6 \(含\) 以後版本來繪製控制項。 如果應用程式是使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 \(含\) 以後版本來建置，則可以使用 <xref:System.Windows.Forms.Application> 類別的 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法。  
  
## 檢查視覺化樣式支援  
 <xref:System.Windows.Forms.Application> 類別的 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 屬性會指出目前的應用程式是否使用視覺化樣式繪製控制項。 在繪製自訂控制項時，您可以檢查 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 的值，以決定是否要使用視覺化樣式呈現控制項。 下表列出四個條件，唯有這些條件成立，<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 才會傳回 `true`。  
  
|條件|備註|  
|--------|--------|  
|作業系統支援視覺化樣式。|若要個別驗證這個條件，請使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> 類別的 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> 屬性。|  
|使用者已經啟用作業系統中的視覺化樣式。|若要個別驗證這個條件，請使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> 類別的 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> 屬性。|  
|已經啟用應用程式中的視覺化樣式。|您可以呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法或使用應用程式資訊清單 \(其中指定使用 ComCtl32.dll 6 \(含\) 以後版本來繪製控制項\)，以啟用應用程式中的視覺化樣式。|  
|正在使用視覺化樣式來繪製應用程式視窗的工作區。|若要個別驗證這個條件，請使用 <xref:System.Windows.Forms.Application> 類別的 <xref:System.Windows.Forms.Application.VisualStyleState%2A> 屬性，並驗證該屬性具有 <xref:System.Windows.Forms.VisualStyles.VisualStyleState?displayProperty=fullName> 或 <xref:System.Windows.Forms.VisualStyles.VisualStyleState?displayProperty=fullName> 值。|  
  
 若要使用者何時啟用或停用視覺化樣式或在視覺化樣式之間相互切換，請檢查 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=fullName> 或 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=fullName> 事件處理常式中的 <xref:Microsoft.Win32.UserPreferenceCategory?displayProperty=fullName> 值。  
  
> [!IMPORTANT]
>  如果您想在使用者啟用或切換視覺化樣式時使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 呈現控制項或 UI 項目，請務必在處理 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件時進行此作業，而不是在處理 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> 事件時這麼做。 如果您在處理 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> 時使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 類別，便會擲回例外狀況。  
  
## 請參閱  
 [自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)