---
title: 如何：使用 OpenFileDialog 元件開啟檔案
ms.date: 02/11/2019
description: 瞭解如何使用 OpenFileDialog 元件開啟 [Windows] 對話方塊，以流覽和選取檔案。
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904425"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>如何：使用 OpenFileDialog 開啟檔案

此 <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> 元件會開啟 [Windows] 對話方塊，供您流覽和選取檔案。 若要開啟和讀取選取的檔案，您可以使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> 方法，或建立類別的實例 <xref:System.IO.StreamReader?displayProperty=nameWithType> 。 下列範例會示範這兩種方法。

在 .NET Framework 中，若要取得或設定 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性，需要由類別授與的許可權層級 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 。 這些範例會執行 <xref:System.Security.Permissions.FileIOPermission> 許可權檢查，而且如果在部分信任內容中執行，可能會因為許可權不足而擲回例外狀況。 如需詳細資訊，請參閱[代碼啟用安全性基本概念](../../misc/code-access-security-basics.md)。

您可以從 c # 或 Visual Basic 命令列 .NET Framework 的應用程式，建立並執行這些範例。 如需詳細資訊，請參閱使用 csc.exe或[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)[的命令列建立](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。

從 .NET Core 3.0 開始，您也可以從具有 .NET Core Windows Forms * \<folder name> .csproj*專案檔的資料夾，將範例建立並執行為 Windows .net core 應用程式。

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>範例：使用 StreamReader 將檔案讀取為數據流  
  
下列範例會使用 Windows Forms <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以 <xref:System.Windows.Forms.OpenFileDialog> 方法開啟 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 。 在使用者選擇檔案並選取 **[確定]** 之後，類別的實例會 <xref:System.IO.StreamReader> 讀取檔案，並在表單的文字方塊中顯示其內容。 如需從檔案資料流程讀取的詳細資訊，請參閱 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> 。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>範例：使用 OpenFile 從篩選後的選取範圍開啟檔案

下列範例 <xref:System.Windows.Forms.Button> 會使用控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，開啟 <xref:System.Windows.Forms.OpenFileDialog> 具有只顯示文字檔的篩選準則。 使用者選擇文字檔並選取 **[確定]** 之後， <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 會使用方法在 [記事本] 中開啟檔案。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 元件](openfiledialog-component-windows-forms.md)
