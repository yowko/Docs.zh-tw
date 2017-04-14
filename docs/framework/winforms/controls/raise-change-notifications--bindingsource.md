---
title: "如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 與 IPropertyChange"
  - "BindingSource 元件 [Windows Form], 範例"
  - "變更告知"
  - "變更告知, 引發"
  - "資料來源, 偵測變更"
  - "範例 [Windows Form], BindingSource 元件"
  - "INotifyPropertyChanged 介面, 與 BindingSource 一起使用"
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知
當資料來源中包含的類型實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，並且在屬性值變更時引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件，<xref:System.Windows.Forms.BindingSource> 元件將會自動偵測資料來源中的變更。  這很有用，因為當資料來源值變更時，繫結至 <xref:System.Windows.Forms.BindingSource> 的控制項就會自動更新。  
  
> [!NOTE]
>  如果您的資料來源實作 <xref:System.ComponentModel.INotifyPropertyChanged>，而您正在執行非同步作業，您就不應該對背景執行緒上的資料來源進行變更。  相反地，您應該讀取背景執行緒上的資料，並將該資料合併至 UI 執行緒上的清單中。  
  
## 範例  
 下列程式碼範例示範 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的簡單實作。  它也會示範當 <xref:System.Windows.Forms.BindingSource> 繫結至 <xref:System.ComponentModel.INotifyPropertyChanged> 類型的清單時，<xref:System.Windows.Forms.BindingSource> 如何自動將資料來源變更傳遞至繫結的控制項。  
  
 如果您使用 `CallerMemberName` 屬性 \(attribute\)，呼叫 `NotifyPropertyChanged` 方法時，不需要指定屬性 \(property\) 名稱做為字串引數。  如需詳細資訊，請參閱[呼叫端資訊](../Topic/Caller%20Information%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.ComponentModel.INotifyPropertyChanged>   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [如何：使用 BindingSource ResetItem 方法引發變更通知](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)