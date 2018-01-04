---
title: "Windows Form 資料繫結中的變更告知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 827e93ad779dfeb2dd398a2fc031fcb99a77a39c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows Form 資料繫結中的變更告知
其中一個最重要的 Windows Form 資料繫結的概念是*變更通知*。 若要確保您的資料來源和繫結的控制項一直擁有最新的資料，您必須加入資料繫結變更通知。 具體來說，您想要確保繫結的控制項的資料來源，所做的變更會收到通知，而且資料來源會通知控制項的繫結的屬性所做的變更。  
  
 有不同種類的變更通知，資料繫結的類型而定：  
  
-   簡單繫結，其中單一的控制項屬性繫結到物件的單一執行個體。  
  
-   清單架構繫結，其中包含單一的控制項屬性繫結至清單中的項目屬性或控制項屬性繫結至的物件清單。  
  
 此外，如果您要建立您想要用於資料繫結的 Windows Form 控制項，您必須套用*PropertyName*控制項，變更模式，使控制項的繫結屬性的變更會傳播至資料來源。  
  
## <a name="change-notification-for-simple-binding"></a>簡單繫結變更通知  
 針對簡單繫結、 繫結屬性的值變更時商務物件時，必須提供變更通知。 您可以藉由公開*PropertyName*您的商務物件和使用的控制項繫結的商務物件的每一個屬性已變更 」 事件<xref:System.Windows.Forms.BindingSource>或您的商務物件會實作的慣用的方法<xref:System.ComponentModel.INotifyPropertyChanged>介面並引發<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件屬性的值變更時發生。 如需詳細資訊，請參閱[How to： 實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)。 當您使用實作物件<xref:System.ComponentModel.INotifyPropertyChanged>介面，您不必使用<xref:System.Windows.Forms.BindingSource>來將物件繫結至控制項，但使用<xref:System.Windows.Forms.BindingSource>建議。  
  
## <a name="change-notification-for-list-based-binding"></a>以清單為基礎的繫結變更通知  
 Windows Form 取決於繫結的清單，來提供 （清單項目屬性值變更） 的屬性變更和已變更的清單 （項目已刪除，或加入至清單） 繫結控制項的資訊。 因此，會列出用於資料繫結必須實作<xref:System.ComponentModel.IBindingList>，這樣會提供兩種類型的變更通知。 <xref:System.ComponentModel.BindingList%601>是以一般的實作<xref:System.ComponentModel.IBindingList>是針對使用 Windows Form 資料繫結所設計。 您可以建立<xref:System.ComponentModel.BindingList%601>，其中包含實作的商務物件類型<xref:System.ComponentModel.INotifyPropertyChanged>和清單會自動將轉換<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件<xref:System.ComponentModel.IBindingList.ListChanged>事件。 如果繫結的清單不是<xref:System.ComponentModel.IBindingList>，您必須使用的物件清單繫結至 Windows Form 控制項<xref:System.Windows.Forms.BindingSource>元件。 <xref:System.Windows.Forms.BindingSource>元件將會提供類似的屬性加入至清單轉換<xref:System.ComponentModel.BindingList%601>。 如需詳細資訊，請參閱[How to： 使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)。  
  
## <a name="change-notification-for-custom-controls"></a>自訂控制項變更通知  
 最後，從控制項端必須將公開*PropertyName*設計來繫結至資料的每一個屬性已變更 」 事件。 控制項屬性的變更會再傳播到繫結的資料來源。 如需詳細資訊，請參閱[如何： 套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows Forms 支援的資料來源](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
