---
title: "多重文件介面 (MDI) 應用程式 | Microsoft Docs"
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
  - "表單, MDI"
  - "MDI"
  - "Windows Form, MDI 應用程式"
  - "視窗, MDI"
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 多重文件介面 (MDI) 應用程式
多重文件介面 \(MDI\) 應用程式能夠讓您同時顯示多份文件，讓各文件顯示在自己的視窗上。  MDI 應用程式通常具有其中包括子功能表的 Windows 功能表項目，用以在視窗或文件之間進行切換。  
  
> [!NOTE]
>  在 Windows Form 中，MDI 表單和單一文件介面 \(SDI\) 視窗之間的行為有些許不同。  `Opacity` 屬性不會影響 MDI 子表單的外觀。  此外，<xref:System.Windows.Forms.Form.CenterToParent%2A> 方法也不會影響 MDI 子表單的行為。  
  
## 在本節中  
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 提供在 MDI 應用程式中建立多重文件的容器說明。  
  
 [如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 提供在 MDI 父表單中建立一個或多個可供操作的視窗的說明。  
  
 [如何：決定作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 提供指示以驗證具有焦點的子視窗 \(並傳送其內容至剪貼簿中\)。  
  
 [如何：傳送資料至作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 提供指示以傳輸資訊至作用中的子視窗中。  
  
 [如何：安排 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 提供指示以並排、重疊或排列顯示 MDI 應用程式的子視窗。