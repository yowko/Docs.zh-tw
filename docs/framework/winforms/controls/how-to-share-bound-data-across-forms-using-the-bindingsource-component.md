---
title: 作法：使用 BindingSource 元件跨表單共用繫結資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956079"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>作法：使用 BindingSource 元件跨表單共用繫結資料
您可以使用 <xref:System.Windows.Forms.BindingSource> 元件輕鬆地跨表單共用資料。 例如，您可能想要顯示一個唯讀表單，該表單會摘要資料來源資料，並顯示另一個可編輯的表單，其中包含在資料來源中目前所選取項目的詳細資訊。 這個範例將示範此案例。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何跨表單共用 <xref:System.Windows.Forms.BindingSource> 及其繫結的資料。 在此範例中，會傳遞共用的 <xref:System.Windows.Forms.BindingSource> 至子表單的建構函式。 子表單可讓使用者在主表單中編輯目前所選取項目的資料。  
  
> [!NOTE]
> 在此範例中，會處理 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以確保這兩個表單維持同步處理。 如需如何完成此作業的詳細資訊, [請參閱如何:請確定系結至相同資料來源的多個](../multiple-controls-bound-to-data-source-synchronized.md)控制項保持同步。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Windows.Forms、System.Drawing、System.Data 和 System.Xml 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- [BindingSource 元件](bindingsource-component.md)
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [如何：處理資料系結時所發生的錯誤和例外狀況](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
