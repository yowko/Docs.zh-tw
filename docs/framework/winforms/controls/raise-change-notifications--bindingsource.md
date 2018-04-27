---
title: 如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de75d4d3d8de34bc85ee47b6761724da93fc0ecc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知
當資料來源中包含的類型實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，並且在屬性值變更時引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件，<xref:System.Windows.Forms.BindingSource> 元件將會自動偵測資料來源中的變更。 這很有用，因為當資料來源值變更時，繫結至 <xref:System.Windows.Forms.BindingSource> 的控制項就會自動更新。  
  
> [!NOTE]
>  如果您的資料來源實作 <xref:System.ComponentModel.INotifyPropertyChanged>，而您正在執行非同步作業，您就不應該對背景執行緒上的資料來源進行變更。 相反地，您應該讀取背景執行緒上的資料，並將該資料合併至 UI 執行緒上的清單中。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的簡單實作。 它也會示範當 <xref:System.Windows.Forms.BindingSource> 繫結至 <xref:System.ComponentModel.INotifyPropertyChanged> 類型的清單時，<xref:System.Windows.Forms.BindingSource> 如何自動將資料來源變更傳遞至繫結的控制項。  
  
 如果您使用 `CallerMemberName` 屬性 (attribute)，呼叫 `NotifyPropertyChanged` 方法時，不需要指定屬性 (property) 名稱做為字串引數。 如需詳細資訊，請參閱[呼叫端資訊](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373)。  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱[超連結"http://msdn.microsoft.com/library/Bb129228(v=vs.110)"如何： 編譯及執行完整 Windows Form 程式碼範例使用 Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [操作說明：使用 BindingSource ResetItem 方法引發變更通知](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
