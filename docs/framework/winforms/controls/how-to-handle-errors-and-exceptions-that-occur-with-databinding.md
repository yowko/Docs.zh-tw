---
title: 如何：處理資料繫結時所發生的錯誤和例外狀況
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 464ceb42416c91ae84c20c65fba2629479b1a0cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>如何：處理資料繫結時所發生的錯誤和例外狀況
當您將它們繫結至控制項時，有時候基礎商務物件會發生例外狀況和錯誤。 您可以攔截這些錯誤和例外狀況然後復原，或藉由為特定的 <xref:System.Windows.Forms.Binding> 、 <xref:System.Windows.Forms.BindingSource> 或 <xref:System.Windows.Forms.CurrencyManager> 元件處理 <xref:System.Windows.Forms.Binding.BindingComplete> 事件，將錯誤資訊傳遞給使用者。  
  
## <a name="example"></a>範例  
 這個程式碼範例會示範如何處理錯誤以及資料繫結作業期間發生的例外狀況。 它示範如何藉由處理 <xref:System.Windows.Forms.Binding> 物件中的 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> 事件來攔截錯誤。 若要藉由處理這個事件來攔截錯誤和例外狀況，您必須為繫結啟用格式化。 您可以於繫結被建構或加到繫結集合中時，或藉由設定 <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> 屬性為 `true` 來啟用格式化。  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 當程式碼正在執行，同時在部分名稱輸入空字串或在部分編號輸入小於 100 的值時，會出現訊息方塊。 這是為了這些文字方塊繫結處理 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> 事件所得到的結果。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)
