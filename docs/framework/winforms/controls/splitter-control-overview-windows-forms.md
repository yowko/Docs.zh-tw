---
title: "Splitter 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Splitter"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Splitter 控制項 [Windows Form], 關於 Splitter 控制項"
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Splitter 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  雖然 <xref:System.Windows.Forms.SplitContainer> 會取代並且將功能加入至之前版本的 <xref:System.Windows.Forms.Splitter> 控制項；不過，也可以選擇保留 <xref:System.Windows.Forms.Splitter>，以提供回溯相容性 \(Backward Compatibility\) 以及供未來使用。  
  
 Windows Form <xref:System.Windows.Forms.Splitter> 控制項的用途在於執行階段重新調整停駐控制項的大小。  <xref:System.Windows.Forms.Splitter> 控制項通常用於內含控制項的表單上，這些控制項會顯示各種長度的資料 \(如 Windows 檔案總管\)，其資料窗格在不同時間會顯示不同寬度的資訊。  
  
## 使用分隔器控制項  
 當使用者將滑鼠指標指向控制項未停駐的邊緣時 \(該控制項可以由分隔器 \(Splitter\) 控制項調整大小\)，指標會變更其外觀，表示可以重新調整控制項的大小。  使用者可以調整緊接在 分隔器控制項前面的停駐控制項的大小。  因此，若要讓使用者在 Run Time 重新調整停駐控制項的大小，請將要重新調整大小的控制項停駐於容器 \(Container\) 的邊緣，然後將 Splitter 控制項停駐於該容器的同一邊。  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [如何：將控制項停駐在 Windows Form 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)