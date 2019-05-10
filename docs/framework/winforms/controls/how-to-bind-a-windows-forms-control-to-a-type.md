---
title: HOW TO：將 Windows Forms 控制項繫結至類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 93cf9844a1c5b9d6eb052c94c2309cbff1f4ad56
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612380"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>HOW TO：將 Windows Forms 控制項繫結至類型
當您在建立與資料互動的控制項時，有時會發現有必要將控制項繫結至類型，而非物件。 特別是在設計階段會發生這種情況，此時資料可能無法使用，但是資料繫結控制項仍然需要顯示類型公用介面中的資訊。 例如，您可能會繫結 <xref:System.Windows.Forms.DataGridView> 控制項至 Web 服務所公開的物件，並想讓 <xref:System.Windows.Forms.DataGridView> 控制項將設計階段的資料行標記為自訂類型的成員名稱。  
  
 您可以輕鬆地繫結控制項至具有 <xref:System.Windows.Forms.BindingSource> 元件的類型。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至自訂類型。 當您執行範例時，您會注意到在控制項填入資料之前，<xref:System.Windows.Forms.DataGridView> 標記會反映 `Customer` 物件屬性的資料行。 此範例包含 [Add Customer] 按鈕，以將資料加入至 <xref:System.Windows.Forms.DataGridView> 控制項。 當您按一下按鈕，新 `Customer` 物件會加入至 <xref:System.Windows.Forms.BindingSource>。 在實際案例中，可能會透過呼叫 Web 服務或其他資料來源取得資料。  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource 元件](bindingsource-component.md)
