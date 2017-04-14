---
title: "如何：使用設計工具建立 Windows Form 控制項的便捷鍵 | Microsoft Docs"
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
  - "便捷鍵, 為控制項建立"
  - "便捷鍵, Windows Form"
  - "ALT 鍵"
  - "快速鍵中的連字號 (&) 字元"
  - "Button 控制項 [Windows Form], 便捷鍵"
  - "控制項 [Windows Form], 便捷鍵"
  - "對話方塊控制項, 助憶鍵"
  - "範例 [Windows Form], 控制項"
  - "鍵盤快速鍵, 為控制項建立"
  - "助憶鍵, 加入至對話方塊控制項"
  - "Text 屬性, 指定控制項的便捷鍵"
  - "Windows Form 控制項, 便捷鍵"
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用設計工具建立 Windows Form 控制項的便捷鍵
*便捷鍵* \(Access Key\) 指的是功能表文字、功能表項目或是控制項標籤中含有底線的字元 \(例如按鈕\)。  便捷鍵可以讓使用者藉由按下 ALT 鍵與預先定義的便捷鍵來完成「按一下」按鈕的動作。  例如，如果某按鈕是以執行程序來列印表單，因此該按鈕 `Text` 屬性是設定為 "Print"，則在字母 "P" 之前加上連字號 \(&\) 即可讓在執行階段的按鈕文字字母 "P" 加上底線。  使用者可按 ALT\+P 鍵來執行與按鈕關聯的命令。  您不能為無法接受焦點的控制項設定便捷鍵。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立控制項的便捷鍵  
  
1.  在 \[**屬性**\] 視窗中，將 `Text` 屬性設定成字串，並在要成為便捷鍵的字母前面加上連字號。  例如，若要將字母 "P" 設定為便捷鍵，請在方格中輸入 &Print。  
  
## 請參閱  
 <xref:System.Windows.Forms.Button>   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)