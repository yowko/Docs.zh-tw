---
title: 資料系結中的變更通知
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746358"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Form 資料繫結中的變更通知
Windows Forms 資料系結的其中一個最重要概念是*變更通知*。 若要確保您的資料來源和繫結控制項一律具有最新的資料，您必須加入資料系結的變更通知。 具體而言，您會想要確保繫結控制項收到其資料來源變更的通知，而資料來源會收到對控制項系結屬性所做變更的通知。  
  
 有不同類型的變更通知，視資料系結類型而定：  
  
- 簡單系結，其中單一控制項屬性會系結至物件的單一實例。  
  
- 以清單為基礎的系結，其中可以包含系結至清單中專案之屬性的單一控制項屬性，或系結至物件清單的控制項屬性。  
  
 此外，如果您要建立要用於資料系結的 Windows Forms 控制項，則必須將*PropertyName*changed 模式套用至控制項，以便將控制項之系結屬性的變更傳播至資料來源。  
  
## <a name="change-notification-for-simple-binding"></a>簡單系結的變更通知  
 針對簡單系結，當系結屬性的值變更時，商務物件必須提供變更通知。 若要這麼做，您可以為商務物件的每個屬性公開*PropertyName*已變更事件，並使用 <xref:System.Windows.Forms.BindingSource> 或慣用方法將商務物件系結至控制項，讓您的商務物件在其中執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，並在屬性的值變更時引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件。 如需詳細資訊，請參閱 how [to：執行 INotifyPropertyChanged 介面](how-to-implement-the-inotifypropertychanged-interface.md)。 當您使用可執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的物件時，您不需要使用 <xref:System.Windows.Forms.BindingSource> 將物件系結至控制項，但建議使用 <xref:System.Windows.Forms.BindingSource>。  
  
## <a name="change-notification-for-list-based-binding"></a>以清單為基礎的系結變更通知  
 Windows Forms 取決於系結清單，以提供屬性變更（清單專案屬性值變更）和清單已變更（專案已刪除或加入清單中）資訊到繫結控制項。 因此，用於資料系結的清單必須執行 <xref:System.ComponentModel.IBindingList>，這會提供兩種類型的變更通知。 <xref:System.ComponentModel.BindingList%601> 是 <xref:System.ComponentModel.IBindingList> 的泛型實作為，而且是設計來搭配 Windows Forms 資料系結使用。 您可以建立 <xref:System.ComponentModel.BindingList%601>，其中包含可執行 <xref:System.ComponentModel.INotifyPropertyChanged> 的商業物件類型，而且清單會自動將 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件轉換成 <xref:System.ComponentModel.IBindingList.ListChanged> 事件。 如果系結清單不是 <xref:System.ComponentModel.IBindingList>，您就必須使用 <xref:System.Windows.Forms.BindingSource> 元件，將物件清單系結至 Windows Forms 控制項。 <xref:System.Windows.Forms.BindingSource> 元件會提供類似于 <xref:System.ComponentModel.BindingList%601>的屬性對清單轉換。 如需詳細資訊，請參閱[如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](./controls/raise-change-notifications--bindingsource.md)。  
  
## <a name="change-notification-for-custom-controls"></a>變更自訂控制項的通知  
 最後，您必須從控制項端公開每個設計要系結至資料之屬性的*PropertyName*已變更事件。 控制項屬性的變更就會傳播到系結的資料來源。 如需詳細資訊，請參閱[如何：套用 PropertyNameChanged 模式](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
- [Windows Forms 支援的資料來源](data-sources-supported-by-windows-forms.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
