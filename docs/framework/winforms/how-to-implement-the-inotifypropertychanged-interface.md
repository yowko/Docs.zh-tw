---
title: "如何：實作 INotifyPropertyChanged 介面 | Microsoft Docs"
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
  - "INotifyPropertyChanged 介面, 實作"
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：實作 INotifyPropertyChanged 介面
下列程式碼範例將示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。  在 Windows Form 資料繫結中所使用的商務物件 \(Business Object\) 中實作此介面。  實作時，介面會通訊至商務物件上其屬性變更的繫結控制項。  
  
## 範例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## 請參閱  
 [如何：套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)   
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)