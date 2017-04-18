---
title: "Windows Form 資料繫結中的變更告知 | Microsoft Docs"
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
  - "Windows Form, 為資料繫結加入變更告知"
  - "Windows Form, 資料繫結"
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Windows Form 資料繫結中的變更告知
Windows Forms 資料繫結的其中一個最重要概念是「*變更告知*」。  若要確保您的資料來源和繫結控制項永遠有最新的資料，您必須為資料繫結加入變更告知。  明確地說，您要確保資料來源變更時繫結控制項會收到告知，以及控制項的繫結屬性變更時資料來源會收到告知。  
  
 變更告知有各種不同類型，視資料繫結的類型而定：  
  
-   簡單繫結 \(Simple Binding\)，指將單一控制項屬性繫結至物件的單一執行個體。  
  
-   清單架構繫結 \(List\-based Binding\)，該繫結可以包含繫結至清單中之項目屬性的單一控制項屬性，或繫結至物件清單的控制項屬性。  
  
 此外，如果您建立的是要做為資料繫結之用的 Windows Form 控制項，則必須將 *PropertyName*Changed 模式套用至控制項，以便將控制項繫結屬性的變更傳送至資料來源。  
  
## 簡單繫結的變更告知  
 若為簡單繫結，商務物件 \(Business Object\) 必須在繫結屬性值變更時提供變更告知。  您可以藉由下列動作完成此目的：公開商務物件之每個屬性的 *PropertyName*Changed 事件，然後將商務物件繫結至具有 <xref:System.Windows.Forms.BindingSource> 或慣用方法的控制項，如此您的商務物件便會實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，並於屬性值變更時引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件。  如需詳細資訊，請參閱 [如何：實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)。  當您使用實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的物件時，您不必使用 <xref:System.Windows.Forms.BindingSource> 來將物件繫結至控制項，但建議使用 <xref:System.Windows.Forms.BindingSource>。  
  
## 清單架構繫結的變更告知  
 Windows Form 會根據繫結清單來提供屬性變更 \(清單項目屬性值變更\) 以及繫結控制項的清單變更 \(已刪除或已加入清單中的項目\) 資訊。  因此，資料繫結所使用的清單必須實作 <xref:System.ComponentModel.IBindingList>，它會提供兩種類型的變更告知。  <xref:System.ComponentModel.BindingList%601> 是 <xref:System.ComponentModel.IBindingList> 的一般實作，其設計是與 Windows Form 資料繫結一起使用。  您可以建立內含會實作 <xref:System.ComponentModel.INotifyPropertyChanged> 之商務物件類型的 <xref:System.ComponentModel.BindingList%601>，而且清單會自動將 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件轉換為 <xref:System.ComponentModel.IBindingList.ListChanged> 事件。  如果繫結清單不是 <xref:System.ComponentModel.IBindingList>，您必須使用 <xref:System.Windows.Forms.BindingSource> 元件，將物件清單繫結至 Windows Form 控制項。  <xref:System.Windows.Forms.BindingSource> 元件會提供類似 <xref:System.ComponentModel.BindingList%601> 轉換的屬性對清單轉換。  如需詳細資訊，請參閱 [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)。  
  
## 自訂控制項的變更告知  
 最後，您必須從控制項端將設計為繫結至資料之每個屬性的 *PropertyName*Changed 事件加以公開。  然後，控制項屬性的變更才會傳送至繫結的資料來源。  如需詳細資訊，請參閱 [如何：套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.ComponentModel.INotifyPropertyChanged>   
 <xref:System.ComponentModel.BindingList%601>   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Windows Form 支援的資料來源](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)