---
title: Windows Form 資料繫結中的變更告知
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: b4a70f96ad256b22ce0d933a633475161160e5a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665846"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Form 資料繫結中的變更告知
其中一個最重要的 Windows Form 資料繫結的概念是*變更通知*。 若要確保您的資料來源和繫結的控制項一律有最新的資料，您必須新增為資料繫結的變更通知。 具體來說，您想要確保繫結的控制項，會通知對他們的資料來源所做的變更，而且對控制項的繫結的屬性所做的變更會通知資料來源。  
  
 有不同類型的變更通知，根據資料繫結的類型：  
  
- 簡單繫結，在其中的單一控制項屬性繫結至物件的單一執行個體。  
  
- 清單架構繫結，其中可以包含單一的控制項屬性繫結到清單中項目的屬性或控制項屬性繫結至物件的清單。  
  
 此外，如果您要建立您想要用於資料繫結的 Windows Form 控制項，您必須套用*PropertyName*控制項，變更模式，使控制項的繫結屬性的變更會傳播至資料來源。  
  
## <a name="change-notification-for-simple-binding"></a>簡單繫結的變更通知  
 簡單的繫結的繫結的屬性值變更時商務物件時，必須提供變更通知。 您可以藉由公開*PropertyName*Changed 事件，您的商務物件和繫結至控制項的商務物件的每一個屬性<xref:System.Windows.Forms.BindingSource>或您的商務物件會實作的慣用的方法<xref:System.ComponentModel.INotifyPropertyChanged>介面，並引發<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件屬性的值變更時。 如需詳細資訊，請參閱[如何：實作 INotifyPropertyChanged 介面](how-to-implement-the-inotifypropertychanged-interface.md)。 當您使用物件，可實作<xref:System.ComponentModel.INotifyPropertyChanged>介面，您就不必使用<xref:System.Windows.Forms.BindingSource>若要將物件繫結至控制項，但使用<xref:System.Windows.Forms.BindingSource>建議。  
  
## <a name="change-notification-for-list-based-binding"></a>以清單為基礎的繫結的變更通知  
 Windows Form 取決於繫結的清單，以提供屬性變更 （變更清單項目屬性值） 和變更的清單 （項目已刪除，或新增到清單中） 對繫結控制項的資訊。 因此，用於資料繫結的清單必須實作<xref:System.ComponentModel.IBindingList>，以提供兩種類型的變更通知。 <xref:System.ComponentModel.BindingList%601>的泛型實作<xref:System.ComponentModel.IBindingList>，適用於使用 Windows Form 資料繫結。 您可以建立<xref:System.ComponentModel.BindingList%601>其中包含商務物件型別可實作<xref:System.ComponentModel.INotifyPropertyChanged>和清單會自動轉換<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件<xref:System.ComponentModel.IBindingList.ListChanged>事件。 如果繫結的清單不是<xref:System.ComponentModel.IBindingList>，您必須使用的物件清單繫結至 Windows Form 控制項<xref:System.Windows.Forms.BindingSource>元件。 <xref:System.Windows.Forms.BindingSource>元件會提供類似的屬性加入至清單轉換<xref:System.ComponentModel.BindingList%601>。 如需詳細資訊，請參閱[如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](./controls/raise-change-notifications--bindingsource.md)。  
  
## <a name="change-notification-for-custom-controls"></a>自訂控制項的變更通知  
 最後，控制來自您必須公開*PropertyName*Changed 事件，每個屬性可繫結至資料。 控制項屬性的變更則會傳播到繫結的資料來源。 如需詳細資訊，請參閱[如何：套用 PropertyNameChanged 模式](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
- [Windows Forms 支援的資料來源](data-sources-supported-by-windows-forms.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
