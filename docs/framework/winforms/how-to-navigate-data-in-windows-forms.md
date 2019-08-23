---
title: 作法：巡覽 Windows Forms 中的資料
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964282"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>HOW TO：巡覽 Windows Forms 中的資料
在 Windows 應用程式中, 流覽資料來源中之記錄的最簡單方式, 就是將<xref:System.Windows.Forms.BindingSource>元件系結至資料來源, 然後將控制項系<xref:System.Windows.Forms.BindingSource>結至。 然後<xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, 您可以在這類、 <xref:System.Windows.Forms.BindingSource.MoveLast%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>和<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>上使用內建的導覽方法。 使用這些方法將會<xref:System.Windows.Forms.BindingSource.Position%2A> <xref:System.Windows.Forms.BindingSource>適當地<xref:System.Windows.Forms.BindingSource.Current%2A>調整的和屬性。 您也可以藉由設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性來尋找專案, 並將它設定為目前的專案。  
  
### <a name="to-increment-the-position-in-a-data-source"></a>若要遞增資料來源中的位置  
  
1. 將系結資料的<xref:System.Windows.Forms.BindingSource> 屬性設為要移至的記錄位置。<xref:System.Windows.Forms.BindingSource.Position%2A> 下列<xref:System.Windows.Forms.BindingSource.MoveNext%2A>範例說明<xref:System.Windows.Forms.BindingSource>如何使用的方法, 在按一下時`nextButton`遞增<xref:System.Windows.Forms.BindingSource.Position%2A>屬性。 會與資料集`Northwind`的`Customers`資料表相關聯。 <xref:System.Windows.Forms.BindingSource>  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A>將屬性設定為超過第一個或最後一筆記錄的值並不會產生錯誤, 因為 .NET Framework 不允許您將位置設定為超出清單界限的值。 如果您的應用程式必須知道您是否已超過第一筆或最後一筆記錄, 請加入邏輯來測試您是否會超出資料元素計數。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>若要檢查您是否已通過結束或開始  
  
1. 建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。 在處理常式中, 您可以測試建議的位置值是否已超過實際的資料元素計數。  
  
     下列範例說明如何測試您是否已到達最後一個資料元素。 在此範例中, 如果您是最後一個元素, 則表單上的 [**下一步]** 按鈕會停用。  
  
    > [!NOTE]
    > 請注意, 如果您要變更在程式碼中流覽的清單, 應該重新啟用 [**下一步]** 按鈕, 讓使用者可以流覽新清單的整個長度。 此外, 請注意<xref:System.Windows.Forms.BindingSource.PositionChanged> , 您所使用之特定<xref:System.Windows.Forms.BindingSource>的事件, 必須與其事件處理方法相關聯。 以下是處理<xref:System.Windows.Forms.BindingSource.PositionChanged>事件的方法範例:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>若要尋找專案並將它設定為目前的專案  
  
1. 尋找您想要設定為目前專案的記錄。 如果您的資料來源已<xref:System.Windows.Forms.BindingSource.Find%2A>完成<xref:System.Windows.Forms.BindingSource>, 您可以使用的方法來執行這項操作。 <xref:System.ComponentModel.IBindingList> 實<xref:System.ComponentModel.IBindingList>作為<xref:System.ComponentModel.BindingList%601>和之資料來源的一些範例。<xref:System.Data.DataView>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 支援的資料來源](data-sources-supported-by-windows-forms.md)
- [Windows Forms 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
