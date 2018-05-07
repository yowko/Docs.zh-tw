---
title: 如何：使用 Windows Forms BindingSource 自訂新增項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 299b24eb42c576535389f53982581bf4a776ee3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>如何：使用 Windows Forms BindingSource 自訂新增項目
當您使用 <xref:System.Windows.Forms.BindingSource> 元件將 Windows Form 控制項繫結至資料來源時，您可能會發現有必要自訂新項目的建立。 <xref:System.Windows.Forms.BindingSource> 元件提供了通常會在繫結控制項需要建立新項目時引發的 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件，使這項作業毫不費力。 您的事件處理常式能夠提供任何要求的自訂行為，例如在 Web 服務上呼叫方法或者從 Class Factory 取得新物件。  
  
> [!NOTE]
>  當您利用處理 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件來加入項目時，這項加入作業將無法取消。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 元件將 <xref:System.Windows.Forms.BindingSource> 控制項繫結至 Class Factory。 當使用者按一下 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列時，就會引發 <xref:System.Windows.Forms.BindingSource.AddingNew> 事件。 事件處理常式將會建立新的 `DemoCustomer` 物件，以指派給 <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> 屬性。 這將使得新的 `DemoCustomer` 物件加入 <xref:System.Windows.Forms.BindingSource> 元件的清單，並於 <xref:System.Windows.Forms.DataGridView> 控制項的新資料列中顯示。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 建置此範例從 visual Basic 或 Visual C# 命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [操作說明：將 Windows Forms 控制項繫結至型別](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
