---
title: 如何：使用 OpenFileDialog 元件打開檔
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182124"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>如何：使用打開檔對話方塊打開檔

元件<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>將打開用於流覽和選擇檔的 Windows 對話方塊。 要打開和讀取所選檔，可以使用 方法<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>或創建類的<xref:System.IO.StreamReader?displayProperty=nameWithType>實例。 以下示例顯示了這兩種方法。

在 .NET 框架中，要獲取<xref:System.Windows.Forms.FileDialog.FileName%2A>或設置該屬性需要<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類授予的權限等級。 這些示例運行<xref:System.Security.Permissions.FileIOPermission>許可權檢查，如果在部分信任上下文中運行，則由於許可權不足，可能會引發異常。 有關詳細資訊，請參閱[代碼訪問安全基礎知識](../../misc/code-access-security-basics.md)。

可以從 C# 或 Visual Basic 命令列生成和運行這些示例為 .NET 框架應用。 有關詳細資訊，請參閱使用[csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。

從 .NET Core 3.0 開始，您還可以從具有 .NET 核心 Windows 表單*\<資料夾名稱>.csproj*專案檔案的資料夾中生成並運行 Windows .NET Core 應用示例。

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>示例：使用流閱讀器將檔作為流讀取  
  
下面的示例使用 Windows 表單<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>的事件處理常式打開 方法 。 <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 使用者選擇檔並選擇 **"確定"** 後，<xref:System.IO.StreamReader>類的實例讀取該檔並在表單的文字方塊中顯示其內容。 有關從檔流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>和<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>示例：使用 OpenFile 從篩選的選擇中打開檔

下面的示例使用<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>的事件處理常式<xref:System.Windows.Forms.OpenFileDialog>打開 僅顯示文字檔的篩選器。 使用者選擇文字檔並選擇 **"確定"** 後，<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>該方法將用於在記事本中打開該檔。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.OpenFileDialog>
- [打開檔對話元件](openfiledialog-component-windows-forms.md)
