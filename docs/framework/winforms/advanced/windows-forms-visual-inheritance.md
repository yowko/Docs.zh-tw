---
title: "Windows Form 視覺繼承 | Microsoft Docs"
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
  - "基底表單"
  - "表單繼承"
  - "繼承"
  - "繼承, 表單"
  - "繼承的表單"
  - "繼承的表單, Windows Form"
  - "Windows Form, 繼承"
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows Form 視覺繼承
在某些情況下，您可能會決定讓某個專案呼叫某個表單，且該表單類似您過去專案中所建立的表單。  或者，您可建立包含各種設定 \(例如浮水印或特定的控制項配置\) 的基本表單，以便於往後專案中使用，而每次的重複動作都包含對原始表單範本所做的修改。  表單的繼承 \(Inheritance\) 可以讓您建立基底表單並從中進行繼承，並且加以修改，不過可同時保留任何您需要的原始設定。  
  
 您可以使用程式設計方式或使用 Visual 繼承選取器建立衍生之類別的表單。  
  
## 在本節中  
 [如何：繼承 Windows Form](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 指示以程式碼建立繼承表單。  
  
 [如何：使用繼承選取器對話方塊繼承表單](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 指示使用繼承選擇器建立繼承表單。  
  
 [修改基底表單外觀的效果](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 指示變更基底 \(base\) 表單的控制項和其屬性。  
  
 [逐步解說：示範視覺化繼承](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 描述如何建立基底 Windows Form 並將它編譯為類別庫。  您會將這個類別庫匯入至其他專案中，並建立繼承自基底表單的新表單。  
  
 [如何：使用修飾詞和 GenerateMember 屬性](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 提供指示以說明如何使用與 Windows Form 設計工具產生元件的成員變數時相關的 `GenerateMember` 和 `Modifiers` 屬性。  
  
## 相關章節  
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)  
 描述如何定義 Visual Basic 類別，以做為其他類別的基礎。  
  
 [Class \- 類別](../Topic/class%20\(C%23%20Reference\).md)  
 描述類別的 C\# 方式，其中允許單一繼承。  
  
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)  
 列出繼承元件中的事件處理常式會產生的常見問題。