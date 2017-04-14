---
title: "如何：鎖定 Windows Form 的控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 鎖定"
  - "Windows Form 控制項, 鎖定"
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：鎖定 Windows Form 的控制項
當設計 Windows 應用程式的使用者介面時，一旦正確放置控制項之後就可以鎖定它們，這樣在設定其他屬性時就不會不慎移動控制項或調整到它們的大小。  
  
 此外，可以立刻鎖定和解除鎖定表單上的所有控制項，這樣對擁有很多控制項的表單是很有幫助的，或者也可以解除鎖定個別控制項。  一旦放置好所有您想放置在表單上的控制項，把它們全部都鎖定位置以避免錯誤的移動。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要鎖定控制項  
  
1.  在 \[**屬性**\] 視窗中，按一下 \[**Locked**\] 屬性並選取 `true` \(按兩下名稱以切換屬性設定\)。  
  
     或者，在控制項上按一下滑鼠右鍵，然後選擇 \[**鎖定控制項**\]。  
  
    > [!NOTE]
    >  鎖定控制項可以防止這些控制項在設計介面上被拖曳至新的大小或位置。  不過，仍然可以使用 \[**屬性**\] 視窗或程式碼，來變更控制項的大小或位置。  
  
### 若要鎖定表單上的所有控制項  
  
1.  從 \[**格式**\] 功能表，選擇 \[**鎖定控制項**\]。  
  
    > [!NOTE]
    >  這個命令也會鎖定表單的大小，因為表單是一個控制項。  
  
### 若要解除鎖定表單上所有鎖定的控制項  
  
1.  從 \[**格式**\] 功能表，選擇 \[**鎖定控制項**\]。  
  
     表單上先前鎖定的所有控制項現在會解除鎖定。  
  
### 若要將鎖定的控制項個別解除鎖定  
  
1.  在 \[**屬性**\] 視窗中，按一下 \[**Locked**\] 屬性並選取 `false` \(按兩下名稱以切換屬性設定\)。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)