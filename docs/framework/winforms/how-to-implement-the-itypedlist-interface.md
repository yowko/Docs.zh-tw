---
title: "如何：實作 ITypedList 介面 | Microsoft Docs"
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
  - "BindingList(Of T) 類別"
  - "資料繫結, 實作"
  - "IBindingList 介面"
  - "ITypedList 介面"
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：實作 ITypedList 介面
實作 <xref:System.ComponentModel.ITypedList> 介面以啟用可繫結清單之結構描述的探索 \(Discovery\)。  
  
## 範例  
 下列程式碼範例示範了如何實作 <xref:System.ComponentModel.ITypedList> 介面。  名為 `SortableBindingList` 的泛型型別是衍生自 <xref:System.ComponentModel.BindingList%601> 類別 \(Class\)，並且會實作 <xref:System.ComponentModel.ITypedList> 介面。  名為 `Customer` 的簡單類別會提供繫結至 <xref:System.Windows.Forms.DataGridView> 控制項之標題的資料。  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## 請參閱  
 <xref:System.ComponentModel.ITypedList>   
 <xref:System.ComponentModel.BindingList%601>   
 <xref:System.ComponentModel.IBindingList>   
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)