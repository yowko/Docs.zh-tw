---
title: "如何：使用 Windows Form BindingNavigator 控制項巡覽資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>如何：使用 Windows Form BindingNavigator 控制項巡覽資料
在 Windows Form 中 <xref:System.Windows.Forms.BindingNavigator> 控制項的問世，可讓開發人員在他們建立的表單上提供使用者簡單資料巡覽和管理使用者介面。  
  
 <xref:System.Windows.Forms.BindingNavigator> 控制項是一種 <xref:System.Windows.Forms.ToolStrip> 控制項，具有預先設定的按鈕，用來巡覽資料集中的第一筆、最後一筆、下一筆和上一筆記錄，以及新增和刪除記錄。 新增按鈕到 <xref:System.Windows.Forms.BindingNavigator> 控制項很容易，因為它是 <xref:System.Windows.Forms.ToolStrip> 控制項。  另請參閱[如何：將載入、儲存和取消按鈕新增至 Windows Forms BindingNavigator 控制項](http://msdn.microsoft.com/library/safa4957\(v=vs.110\))。  
  
 對於每個 <xref:System.Windows.Forms.BindingNavigator> 控制項上的按鈕，並沒有對應於可以程式設計的方式進行相同功能的 <xref:System.Windows.Forms.BindingSource> 元件成員。 例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。 因此，啟用 <xref:System.Windows.Forms.BindingNavigator> 控制項來巡覽資料記錄相當簡單，如同在表單上設定其 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性為適當的 <xref:System.Windows.Forms.BindingSource> 元件。  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>若要設定 BindingNavigator 控制項  
  
1.  新增命名為 `bindingSource1` 的 <xref:System.Windows.Forms.BindingSource> 元件和名為 `textBox1` 和 `textBox2` 的兩個 <xref:System.Windows.Forms.TextBox> 控制項。  
  
2.  將 `bindingSource1` 繫結至資料，並將文字方塊控制項繫結至 `bindingSource1`。 若要執行此工作，請將下列程式碼貼到您的表單並從表單的建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `LoadData`。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  新增名為 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator> 控制項至您的表單。  
  
4.  將 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性設定為 `bindingSource1`。 您可以用設計工具或在程式碼中執行這項操作。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>範例  
 下列程式碼範例是先前所列步驟的完整範例。  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
