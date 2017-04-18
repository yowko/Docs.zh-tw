---
title: "如何：建立顯示進度的 Windows Form 控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 建立"
  - "控制項 [Windows Form], 追蹤進度"
  - "FlashTrackBar 自訂控制項"
  - "進度, 報告 [Windows Form]"
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：建立顯示進度的 Windows Form 控制項
下列程式碼範例會示範名為 `FlashTrackBar`、可用來顯示應用程式層級或進度給使用者的自訂控制項。  它使用漸層以視覺化方式表示進度。  
  
 `FlashTrackBar` 控制項將說明下列的概念。  
  
-   定義自訂屬性。  
  
-   定義自訂事件   \(`FlashTrackBar` 會定義 `ValueChanged` 事件\)。  
  
-   覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法以提供描繪控制項的邏輯。  
  
-   使用控制項的 <xref:System.Windows.Forms.Control.ClientRectangle%2A> 屬性來計算可供描繪的區域。  `FlashTrackBar` 則在其 `OptimizedInvalidate` 方法中執行這項工作。  
  
-   當屬性在 Windows Form 設計工具中變更後，實作該屬性的序列化或持續性。  `FlashTrackBar` 會定義 `ShouldSerializeStartColor` 和 `ShouldSerializeEndColor` 方法以序列化其 `StartColor` 和 `EndColor` 屬性。  
  
 下列資料表顯示由 `FlashTrackBar` 所定義的自訂屬性。  
  
|屬性|描述|  
|--------|--------|  
|`AllowUserEdit`|表示使用者是否可以經由按一下並拖曳快速追蹤列的方式來變更它的值。|  
|`EndColor`|指定追蹤列的結束色彩。|  
|`DarkenBy`|指定相較於前景漸層的背景暗度。|  
|`Max`|指定追蹤列的最大值。|  
|`Min`|指定追蹤列的最小值。|  
|`StartColor`|指定漸層的起始色彩。|  
|`ShowPercentage`|表示是否要顯示漸層的百分比。|  
|`ShowValue`|表示是否要顯示漸層的目前值。|  
|`ShowGradient`|表示追蹤列是否要顯示目前值的色彩漸層。|  
|-   `Value`|指定追蹤列的目前值。|  
  
 下列資料表顯示由屬性變更事件 `FlashTrackBar:` 和引發該事件的方法所定義的其他成員。  
  
|成員|描述|  
|--------|--------|  
|`ValueChanged`|當追蹤列的 `Value` 屬性變更時所引發的事件。|  
|`OnValueChanged`|會引發 `ValueChanged` 事件的方法。|  
  
> [!NOTE]
>  `FlashTrackBar` 使用事件資料的 <xref:System.EventArgs> 類別和事件委派 \(Delegate\) 的 <xref:System.EventHandler>。  
  
 若要處理對應的 *EventName* 事件，`FlashTrackBar` 會覆寫下列繼承自 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的方法：  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 若要處理對應的屬性變更事件，`FlashTrackBar` 會覆寫下列繼承自 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的方法。  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## 範例  
 `FlashTrackBar` 控制項定義了顯示於下列程式碼清單中的兩個 UI 型別編輯器 \(`FlashTrackBarValueEditor` 和 `FlashTrackBarDarkenByEditor`\)。  `HostApp` 類別使用在 Window Form 上的 `FlashTrackBar` 控制項。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## 請參閱  
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [Windows Form 控制項開發的基本概念](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)