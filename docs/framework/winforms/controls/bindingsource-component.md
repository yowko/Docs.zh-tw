---
title: BindingSource 元件
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717592"
---
# <a name="bindingsource-component"></a>BindingSource 元件
封裝資料來源以繫結至控制項。  
  
 <xref:System.Windows.Forms.BindingSource> 元件有兩種用途。 首先，在將表單上的控制項繫結至資料時，它會提供一層間接取值。 其作法是將 <xref:System.Windows.Forms.BindingSource> 元件繫結至您的資料來源，然後將表單上的控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件。 與資料的所有進一步互動，包括巡覽、排序、篩選和更新，都會透過呼叫 <xref:System.Windows.Forms.BindingSource> 元件來完成。  
  
 第二，<xref:System.Windows.Forms.BindingSource> 元件可以做為強類型資料來源。 使用 <xref:System.Windows.Forms.BindingSource.Add%2A> 方法將類型加入 <xref:System.Windows.Forms.BindingSource> 元件時，會建立該類型的清單。  
  
## <a name="in-this-section"></a>本節內容  
 [BindingSource 元件概觀](bindingsource-component-overview.md)  
 介紹 <xref:System.Windows.Forms.BindingSource> 元件的一般概念，此元件可讓您將資料來源繫結至控制項。  
  
 [如何：Windows Forms 控制項繫結至 DBNull 資料庫值](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來處理來自該資料來源的 <xref:System.DBNull> 值。  
  
 [如何：排序和篩選 ADO.NET 資料，使用 Windows Form BindingSource 元件](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，將排序和篩選套用至所顯示的資料。  
  
 [如何：Web 服務使用 Windows Forms BindingSource 繫結](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 Web 服務。  
  
 [如何：處理錯誤和資料繫結時所發生例外狀況](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，正常處理資料繫結作業中發生的錯誤。  
  
 [如何：將 Windows Forms 控制項繫結至型別](how-to-bind-a-windows-forms-control-to-a-type.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至類型。  
  
 [如何：將 Windows Forms 控制項繫結至 Factory 物件](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 Factory 物件或方法。  
  
 [如何：自訂使用 Windows Forms BindingSource 的新增項目](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來建立新的項目，並將其加入資料來源中。  
  
 [如何：使用 BindingSource ResetItem 方法引發變更通知](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，針對不支援變更通知的資料來源，引發變更通知事件。  
  
 [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](raise-change-notifications--bindingsource.md)  
 示範如何使用繼承自 <xref:System.ComponentModel.INotifyPropertyChanged>，具有 <xref:System.Windows.Forms.BindingSource> 控制項的類型。  
  
 [如何：反映 Windows Form 控制項使用 BindingSource 中的資料來源更新](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件來回應資料來源中的變更。  
  
 [如何：使用 BindingSource 元件跨表單共用繫結的資料](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 示範如何使用 <xref:System.Windows.Forms.BindingSource> 將多個表單繫結至相同的資料來源。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.BindingSource>  
 提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 提供 <xref:System.Windows.Forms.BindingNavigator> 控制項的參考文件。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms 資料繫結](../windows-forms-data-binding.md)  
 包含描述 Windows Form 資料繫結架構的主題連結。  
  
 另請參閱[在 Visual Studio 中將控制項繫結至資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。
