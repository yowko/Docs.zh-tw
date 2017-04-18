---
title: "如何：偵測 TextBox 中的文字何時變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵測文字變更"
  - "文字變更, 偵測"
  - "TextBox 控制項, 偵測文字變更"
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：偵測 TextBox 中的文字何時變更
本範例顯示如何使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件，在每次 <xref:System.Windows.Controls.TextBox> 控制項中的文字變更時就執行方法。  
  
 針對包含要監視是否變更之 <xref:System.Windows.Controls.TextBox> 控制項的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在其程式碼後置類別中插入方法，每當 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件引發便會呼叫該方法。  此方法必須擁有與 <xref:System.Windows.Controls.TextChangedEventHandler> 委派所預期相符的簽章。  
  
 每當 <xref:System.Windows.Controls.TextBox> 控制項的內容變更，不論是由使用者變更或以程式方式變更，就會呼叫該事件處理常式。  
  
 **注意：**當 <xref:System.Windows.Controls.TextBox> 控制項建立並在一開始填入文字時，會引發此事件。  
  
## 範例  
 在定義 <xref:System.Windows.Controls.TextBox> 控制項的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，指定值與事件處理常式方法名稱相符的 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 屬性。  
  
 [!code-xml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## 範例  
 針對包含要監視是否變更之 <xref:System.Windows.Controls.TextBox> 控制項的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在其程式碼後置類別中插入方法，每當 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件引發便會呼叫該方法。  此方法必須擁有與 <xref:System.Windows.Controls.TextChangedEventHandler> 委派所預期相符的簽章。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 每當 <xref:System.Windows.Controls.TextBox> 控制項的內容變更，不論是由使用者變更或以程式方式變更，就會呼叫該事件處理常式。  
  
 **注意：**當 <xref:System.Windows.Controls.TextBox> 控制項建立並在一開始填入文字時，會引發此事件。  
  
 註解  
  
## 請參閱  
 <xref:System.Windows.Controls.TextChangedEventArgs>   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)