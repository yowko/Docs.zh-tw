---
title: HOW TO：使用 BindingSource 元件跨表單共用繫結資料
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
ms.openlocfilehash: 19505c690728147d2a67c26371e1cea4c281ab08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154865"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>HOW TO：使用 BindingSource 元件跨表單共用繫結資料
您可以使用 <xref:System.Windows.Forms.BindingSource> 元件輕鬆地跨表單共用資料。 例如，您可能想要顯示一個唯讀表單，該表單會摘要資料來源資料，並顯示另一個可編輯的表單，其中包含在資料來源中目前所選取項目的詳細資訊。 這個範例將示範此案例。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何跨表單共用 <xref:System.Windows.Forms.BindingSource> 及其繫結的資料。 在此範例中，會傳遞共用的 <xref:System.Windows.Forms.BindingSource> 至子表單的建構函式。 子表單可讓使用者在主表單中編輯目前所選取項目的資料。  
  
> [!NOTE]
>  在此範例中，會處理 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以確保這兩個表單維持同步處理。 此動作之原因的詳細資訊，請參閱[How to:請確定多個控制項繫結至相同的資料來源都能保持同步](../multiple-controls-bound-to-data-source-synchronized.md)。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Windows.Forms、System.Drawing、System.Data 和 System.Xml 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- [BindingSource 元件](bindingsource-component.md)
- [Windows Form 資料繫結](../windows-forms-data-binding.md)
- [HOW TO：處理資料繫結發生的錯誤和例外狀況](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
