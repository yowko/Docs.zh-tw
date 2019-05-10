---
title: HOW TO：管理 Windows Forms DataGridView 控制項中的資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating rows
- data grids [Windows Forms], manipulating rows
- rows [Windows Forms], manipulating on Windows Forms
ms.assetid: 522d8944-e073-4488-9673-923f0a8d7214
ms.openlocfilehash: 23591bf6948800f2394e3df8d65ccd055fdde69c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649258"
---
# <a name="how-to-manipulate-rows-in-the-windows-forms-datagridview-control"></a>HOW TO：管理 Windows Forms DataGridView 控制項中的資料列
下列程式碼範例顯示使用 <xref:System.Windows.Forms.DataGridViewRow> 類別屬性操作 <xref:System.Windows.Forms.DataGridView> 資料列的各種方式。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewRowDemo.cpp#200)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewRowDemo.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewrowdemo.vb#200)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](programming-with-cells-rows-and-columns-in-the-datagrid.md)
