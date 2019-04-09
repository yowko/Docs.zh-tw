---
title: HOW TO：使用 OpenFileDialog 元件開啟檔案
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 7f4e96f1714a182647665f12e29d38f2b8037478
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159103"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>HOW TO：使用 OpenFileDialog 開啟的檔案 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>元件就會開啟 [Windows] 對話方塊中，瀏覽和選取的檔案。 若要開啟並讀取選取的檔案，您可以使用<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>方法，或建立的執行個體<xref:System.IO.StreamReader?displayProperty=nameWithType>類別。 下列範例會示範這兩種方法。 

在.NET Framework 中，取得或設定<xref:System.Windows.Forms.FileDialog.FileName%2A>屬性需要特殊權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。 這些範例會執行<xref:System.Security.Permissions.FileIOPermission>權限檢查，並可以擲回的例外狀況，因為沒有足夠的權限，部分信任內容中執行。 如需詳細資訊，請參閱 <<c0> [ 程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。

您可以建置並執行這些範例做為.NET Framework 應用程式，從C#或 Visual Basic 命令列。 如需詳細資訊，請參閱 <<c0> [ 使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。 

從.NET Core 3.0 開始，您可以也建立並執行範例當做 Windows.NET Core 應用程式從資料夾具有.NET Core 的 Windows Forms *\<資料夾名稱 >.csproj*專案檔。 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>範例：做為 streamreader 的資料流讀取的檔案  
  
下列範例會使用 Windows Form<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>若要開啟 事件處理常式<xref:System.Windows.Forms.OpenFileDialog>使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。 使用者選擇的檔案，並選取後 **[確定]**，執行個體<xref:System.IO.StreamReader>類別讀取檔案，並在表單的文字方塊中顯示其內容。 如需從檔案資料流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>和<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>範例：從以 OpenFile 篩選選取範圍開啟檔案 

下列範例會使用<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，以開啟<xref:System.Windows.Forms.OpenFileDialog>可顯示只是文字檔案的篩選。 使用者選擇的文字檔案，並選取後 **[確定]**，則<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法用來在記事本中開啟檔案。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 元件](openfiledialog-component-windows-forms.md)
