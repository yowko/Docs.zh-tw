---
title: 如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知
ms.date: 03/30/2017
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
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739691"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知
當<xref:System.Windows.Forms.BindingSource>資料來源中包含的類型<xref:System.ComponentModel.INotifyPropertyChanged>實現 時,元件會自動偵測數據來源中的更改,並在更改屬性值<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>時引發事件。 此更改檢測很有用,因為綁定到<xref:System.Windows.Forms.BindingSource>的控制項會隨著資料源值的變化而自動更新。  
  
> [!NOTE]
> 如果您的資料來源實作 <xref:System.ComponentModel.INotifyPropertyChanged>，而您正在執行非同步作業，您就不應該對背景執行緒上的資料來源進行變更。 相反地，您應該讀取背景執行緒上的資料，並將該資料合併至 UI 執行緒上的清單中。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的簡單實作。 它也會示範當 <xref:System.Windows.Forms.BindingSource> 繫結至 <xref:System.ComponentModel.INotifyPropertyChanged> 類型的清單時，<xref:System.Windows.Forms.BindingSource> 如何自動將資料來源變更傳遞至繫結的控制項。  
  
 如果您使用 `CallerMemberName` 屬性 (attribute)，呼叫 `NotifyPropertyChanged` 方法時，不需要指定屬性 (property) 名稱做為字串引數。 有關詳細資訊,請參閱[呼叫者資訊 (C#)](../../../csharp/language-reference/attributes/caller-information.md)或[呼叫者資訊(可視基本)。](../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 對系統、系統、資料、系統、繪圖和系統.Windows.窗體程式集的引用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [繫結來源元件](bindingsource-component.md)
- [如何：使用 BindingSource ResetItem 方法引發變更通知](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
