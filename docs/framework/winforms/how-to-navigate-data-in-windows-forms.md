---
title: HOW TO：巡覽 Windows Forms 中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: fb5747ec3c6b640821e4875d86273467eeb922df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154592"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>HOW TO：巡覽 Windows Forms 中的資料
在 Windows 應用程式中，瀏覽資料來源中記錄的最簡單方式是繫結<xref:System.Windows.Forms.BindingSource>元件至資料來源，然後將控制項繫結至<xref:System.Windows.Forms.BindingSource>。 然後您可以使用內建的巡覽方法上<xref:System.Windows.Forms.BindingSource>這類<xref:System.Windows.Forms.BindingSource.MoveNext%2A>， <xref:System.Windows.Forms.BindingSource.MoveLast%2A>，<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>和<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>。 使用這些方法會自動調整<xref:System.Windows.Forms.BindingSource.Position%2A>並<xref:System.Windows.Forms.BindingSource.Current%2A>屬性的<xref:System.Windows.Forms.BindingSource>適當。 您也可以尋找項目，並將它設為目前的項目中，藉由設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性。  
  
### <a name="to-increment-the-position-in-a-data-source"></a>要遞增的資料來源中的位置  
  
1.  設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性<xref:System.Windows.Forms.BindingSource>繫結資料移至的記錄位置。 下列範例說明如何利用<xref:System.Windows.Forms.BindingSource.MoveNext%2A>方法<xref:System.Windows.Forms.BindingSource>遞增<xref:System.Windows.Forms.BindingSource.Position%2A>屬性時`nextButton`按下。 <xref:System.Windows.Forms.BindingSource>相關聯`Customers`資料表的資料集`Northwind`。  
  
    > [!NOTE]
    >  設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性設為值之外的第一個或最後一筆記錄不會導致發生錯誤時，為[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]將不允許您將位置設定的值超出清單的範圍。 如果您知道是否您已經看過的第一個或最後一筆記錄的應用程式中很重要，，包括邏輯，以測試是否就會超出資料元素計數。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>若要檢查是否已通過結尾或開頭  
  
1.  建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。 在處理常式中，您可以測試是否建議的位置值已超過實際的資料元素計數。  
  
     下列範例說明如何測試是否已到達最後一個資料元素。 在範例中，如果您在最後一個元素，**下一步**表單上的按鈕已停用。  
  
    > [!NOTE]
    >  請注意，您應該變更您瀏覽程式碼中的清單，您應該重新啟用**下一步**按鈕，以便使用者可以瀏覽新的清單中的整個長度。 此外，請注意，上述<xref:System.Windows.Forms.BindingSource.PositionChanged>特定的事件<xref:System.Windows.Forms.BindingSource>您正在使用必須為其事件處理方法相關聯。 以下是針對處理方法的範例<xref:System.Windows.Forms.BindingSource.PositionChanged>事件：  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>尋找項目，並將它設為目前的項目  
  
1.  尋找您想要設定為目前的項目記錄。 您可以使用<xref:System.Windows.Forms.BindingSource.Find%2A>方法<xref:System.Windows.Forms.BindingSource>，如果您的資料來源實作<xref:System.ComponentModel.IBindingList>。 資料的一些範例來源可實<xref:System.ComponentModel.IBindingList>都<xref:System.ComponentModel.BindingList%601>和<xref:System.Data.DataView>。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 支援的資料來源](data-sources-supported-by-windows-forms.md)
- [Windows Form 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
- [資料繫結和 Windows Form](data-binding-and-windows-forms.md)
- [Windows Form 資料繫結](windows-forms-data-binding.md)
