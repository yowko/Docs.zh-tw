---
title: "使用 ImeMode 屬性顯示亞洲字元 | Microsoft Docs"
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
  - "亞洲語言"
  - "亞洲語言, 以 ImeMode 顯示"
  - "中文字元, 以 ImeMode 顯示"
  - "全球化 [Windows Form], 字元集"
  - "IME 模式"
  - "IMEMode 屬性"
  - "輸入法 (IME), 模式"
  - "國際應用程式 [Windows Form], 字元顯示"
  - "國際字元"
  - "日文字元, 以 ImeMode 顯示"
  - "韓文字元"
  - "當地語系化 [Windows Form], 字元集"
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 使用 ImeMode 屬性顯示亞洲字元
表單和控制項會使用 <xref:System.Windows.Forms.Control.ImeMode%2A> 屬性來強制執行輸入法 \(IME\) 的特定模式。  IME 是撰寫中文、日文和韓文指令碼的重要元件，因為這些撰寫系統的字元多於標準鍵盤可編碼的字元。  例如，您可能想要在特殊文字方塊中只允許 ASCII 字元。  在這種情況下，您可以將 <xref:System.Windows.Forms.Control.ImeMode%2A> 屬性設定為 <xref:System.Windows.Forms.ImeMode>，那麼使用者就只能在該特定文字方塊中輸入 ASCII 字元。  <xref:System.Windows.Forms.Control.ImeMode%2A> 屬性的預設值為 <xref:System.Windows.Forms.ImeMode>，所以如果您為表單設定這個屬性，則表單上所有的控制項都會繼承該設定值。  如需詳細資訊，請參閱 [Control.ImeMode 屬性](frlrfSystemWindowsFormsControlClassImeModeTopic)和 [ImeMode 列舉型別](frlrfSystemWindowsFormsImeModeClassTopic)。  
  
## 請參閱  
 [全球化 Windows Form](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)