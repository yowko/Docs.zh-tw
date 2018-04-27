---
title: 如何：停用 Windows Form DataGridView 控制項按鈕資料行中的按鈕
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
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4511441e3d8350cd867133a87f34fcba3087f796
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>如何：停用 Windows Form DataGridView 控制項按鈕資料行中的按鈕
<xref:System.Windows.Forms.DataGridView> 控制項包含 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，可使用按鈕等使用者介面 (UI) 來顯示儲存格。 但是，<xref:System.Windows.Forms.DataGridViewButtonCell> 未提供任何方法，來停用儲存格所顯示的按鈕外觀。  
  
 下列程式碼範例示範如何自訂 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，來顯示可呈現為停用狀態的按鈕。 這個範例會定義新的儲存格類型 `DataGridViewDisableButtonCell`，這個類型衍生自 <xref:System.Windows.Forms.DataGridViewButtonCell>。 這個儲存格類型提供了新的 `Enabled` 屬性，可設定為 `false`，以便在儲存格中繪製停用的按鈕。 這個範例也會定義新的資料行類型 `DataGridViewDisableButtonColumn`，以顯示 `DataGridViewDisableButtonCell` 物件。 為了示範這個新的儲存格和資料行類型，在父 <xref:System.Windows.Forms.DataGridView> 中每個 <xref:System.Windows.Forms.DataGridViewCheckBoxCell> 的目前值會決定同一個資料列中 `DataGridViewDisableButtonCell` 的 `Enabled` 屬性是 `true` 或 `false`。  
  
> [!NOTE]
>  當您從 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 衍生並將新屬性加入衍生類別時，請務必覆寫 `Clone` 方法，以便於複製作業期間複製新屬性。 您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing、System.Windows.Forms 和 System.Windows.Forms.VisualStyles 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows Forms DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
