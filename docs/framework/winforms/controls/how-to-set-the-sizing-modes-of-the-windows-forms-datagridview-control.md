---
title: HOW TO：設定 Windows Forms DataGridView 控制項的調整大小模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: d92322da6644c110f5e3177acebea62799a0ed89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013097"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>HOW TO：設定 Windows Forms DataGridView 控制項的調整大小模式
下列程序示範一些常見的情況，這些自訂或結合可用的調整大小選項以供 <xref:System.Windows.Forms.DataGridView> 控制項以及控制項中的特定資料行使用。  
  
### <a name="to-create-a-fixed-width-column"></a>建立固定寬度資料行  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> 、 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewTriState.False> 、 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性設為 `true` 和 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 屬性設為適當值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>建立會自動調整其大小以符合其內容的資料行  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性設定為以內容為基礎的大小調整模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>建立不同的大小和重要性的值填滿模式資料行  
  
-   設定 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>來為所有不會覆寫此值的資料行設定大小調整模式。 將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性，依照它們的平均內容寬度找出適當比例，做為設定值。 設定重要性資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性，以確保會顯示部分內容。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>範例  
 下列的完整程式碼範例提供示範用應用程式，可以協助您了解本主題中所述的大小調整選項。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 使用本示範應用程式：  
  
-   變更表單的大小 觀察填滿模式資料行在由 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值指定並保留比例時如何變更其寬度。 觀察資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 如何在表單太小時防止其變更。  
  
-   使用滑鼠拖曳資料行分隔線來變更資料行大小。 觀察某些資料行為何不能調整大小，以及可調整大小的資料行為何不能設定成比最小寬度還窄。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
