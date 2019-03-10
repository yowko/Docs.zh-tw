---
title: HOW TO：使用 Windows Forms BindingNavigator 控制項巡覽資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 5fd1caabbc876d5b71deae2d9b1b9cf232d17700
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723240"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>HOW TO：使用 Windows Forms BindingNavigator 控制項巡覽資料
在 Windows Form 中 <xref:System.Windows.Forms.BindingNavigator> 控制項的問世，可讓開發人員在他們建立的表單上提供使用者簡單資料巡覽和管理使用者介面。  
  
 <xref:System.Windows.Forms.BindingNavigator> 控制項是一種 <xref:System.Windows.Forms.ToolStrip> 控制項，具有預先設定的按鈕，用來巡覽資料集中的第一筆、最後一筆、下一筆和上一筆記錄，以及新增和刪除記錄。 新增按鈕到 <xref:System.Windows.Forms.BindingNavigator> 控制項很容易，因為它是 <xref:System.Windows.Forms.ToolStrip> 控制項。 如需範例，請參閱[如何：將載入、 儲存，和 [取消] 按鈕，以 Windows Forms BindingNavigator 控制項](load-save-and-cancel-bindingnavigator.md)。  
  
 對於每個 <xref:System.Windows.Forms.BindingNavigator> 控制項上的按鈕，並沒有對應於可以程式設計的方式進行相同功能的 <xref:System.Windows.Forms.BindingSource> 元件成員。 例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。 因此，啟用 <xref:System.Windows.Forms.BindingNavigator> 控制項來巡覽資料記錄相當簡單，如同在表單上設定其 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性為適當的 <xref:System.Windows.Forms.BindingSource> 元件。  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>若要設定 BindingNavigator 控制項  
  
1.  新增命名為 `bindingSource1` 的 <xref:System.Windows.Forms.BindingSource> 元件和名為 `textBox1` 和 `textBox2` 的兩個 <xref:System.Windows.Forms.TextBox> 控制項。  
  
2.  將 `bindingSource1` 繫結至資料，並將文字方塊控制項繫結至 `bindingSource1`。 若要執行此工作，請將下列程式碼貼到您的表單並從表單的建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `LoadData`。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  新增名為 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator> 控制項至您的表單。  
  
4.  將 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性設定為 `bindingSource1`。 您可以用設計工具或在程式碼中執行這項操作。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>範例  
 下列程式碼範例是先前所列步驟的完整範例。  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
