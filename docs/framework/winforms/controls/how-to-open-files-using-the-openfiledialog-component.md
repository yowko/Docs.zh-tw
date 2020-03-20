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
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="3fdbb-102">如何：使用打開檔對話方塊打開檔</span><span class="sxs-lookup"><span data-stu-id="3fdbb-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="3fdbb-103">元件<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>將打開用於流覽和選擇檔的 Windows 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="3fdbb-104">要打開和讀取所選檔，可以使用 方法<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>或創建類的<xref:System.IO.StreamReader?displayProperty=nameWithType>實例。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3fdbb-105">以下示例顯示了這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-105">The following examples show both approaches.</span></span>

<span data-ttu-id="3fdbb-106">在 .NET 框架中，要獲取<xref:System.Windows.Forms.FileDialog.FileName%2A>或設置該屬性需要<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類授予的權限等級。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3fdbb-107">這些示例運行<xref:System.Security.Permissions.FileIOPermission>許可權檢查，如果在部分信任上下文中運行，則由於許可權不足，可能會引發異常。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="3fdbb-108">有關詳細資訊，請參閱[代碼訪問安全基礎知識](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="3fdbb-109">可以從 C# 或 Visual Basic 命令列生成和運行這些示例為 .NET 框架應用。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="3fdbb-110">有關詳細資訊，請參閱使用[csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="3fdbb-111">從 .NET Core 3.0 開始，您還可以從具有 .NET 核心 Windows 表單*\<資料夾名稱>.csproj*專案檔案的資料夾中生成並運行 Windows .NET Core 應用示例。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="3fdbb-112">示例：使用流閱讀器將檔作為流讀取</span><span class="sxs-lookup"><span data-stu-id="3fdbb-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="3fdbb-113">下面的示例使用 Windows 表單<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>的事件處理常式打開 方法 。 <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A></span><span class="sxs-lookup"><span data-stu-id="3fdbb-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="3fdbb-114">使用者選擇檔並選擇 **"確定"** 後，<xref:System.IO.StreamReader>類的實例讀取該檔並在表單的文字方塊中顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="3fdbb-115">有關從檔流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>和<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="3fdbb-116">示例：使用 OpenFile 從篩選的選擇中打開檔</span><span class="sxs-lookup"><span data-stu-id="3fdbb-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="3fdbb-117">下面的示例使用<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>的事件處理常式<xref:System.Windows.Forms.OpenFileDialog>打開 僅顯示文字檔的篩選器。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="3fdbb-118">使用者選擇文字檔並選擇 **"確定"** 後，<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>該方法將用於在記事本中打開該檔。</span><span class="sxs-lookup"><span data-stu-id="3fdbb-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="3fdbb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fdbb-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="3fdbb-120">打開檔對話元件</span><span class="sxs-lookup"><span data-stu-id="3fdbb-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
