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
ms.openlocfilehash: f297b557e86c13c00a57a2033ba4cd61753b3d0b
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202648"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="90dba-102">HOW TO：使用 OpenFileDialog 開啟的檔案</span><span class="sxs-lookup"><span data-stu-id="90dba-102">How to: Open files with the OpenFileDialog</span></span> 

<span data-ttu-id="90dba-103"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>元件就會開啟 [Windows] 對話方塊中，瀏覽和選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="90dba-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="90dba-104">若要開啟並讀取選取的檔案，您可以使用<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>方法，或建立的執行個體<xref:System.IO.StreamReader?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="90dba-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="90dba-105">下列範例會示範這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="90dba-105">The following examples show both approaches.</span></span> 

<span data-ttu-id="90dba-106">在.NET Framework 中，取得或設定<xref:System.Windows.Forms.FileDialog.FileName%2A>屬性需要特殊權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="90dba-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="90dba-107">這些範例會執行<xref:System.Security.Permissions.FileIOPermission>權限檢查，並可以擲回的例外狀況，因為沒有足夠的權限，部分信任內容中執行。</span><span class="sxs-lookup"><span data-stu-id="90dba-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="90dba-108">如需詳細資訊，請參閱 <<c0> [ 程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="90dba-108">For more information, see [Code access security basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="90dba-109">您可以建置並執行這些範例做為.NET Framework 應用程式，從C#或 Visual Basic 命令列。</span><span class="sxs-lookup"><span data-stu-id="90dba-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="90dba-110">如需詳細資訊，請參閱 <<c0> [ 使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="90dba-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="90dba-111">從.NET Core 3.0 開始，您可以也建立並執行範例當做 Windows.NET Core 應用程式從資料夾具有.NET Core 的 Windows Forms *\<資料夾名稱 >.csproj*專案檔。</span><span class="sxs-lookup"><span data-stu-id="90dba-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="90dba-112">範例：做為 streamreader 的資料流讀取的檔案</span><span class="sxs-lookup"><span data-stu-id="90dba-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="90dba-113">下列範例會使用 Windows Form<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>若要開啟 事件處理常式<xref:System.Windows.Forms.OpenFileDialog>使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="90dba-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="90dba-114">使用者選擇的檔案，並選取後 **[確定]**，執行個體<xref:System.IO.StreamReader>類別讀取檔案，並在表單的文字方塊中顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="90dba-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="90dba-115">如需從檔案資料流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>和<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="90dba-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](../../../../samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](../../../../samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="90dba-116">範例：從以 OpenFile 篩選選取範圍開啟檔案</span><span class="sxs-lookup"><span data-stu-id="90dba-116">Example: Open a file from a filtered selection with OpenFile</span></span> 

<span data-ttu-id="90dba-117">下列範例會使用<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，以開啟<xref:System.Windows.Forms.OpenFileDialog>可顯示只是文字檔案的篩選。</span><span class="sxs-lookup"><span data-stu-id="90dba-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="90dba-118">使用者選擇的文字檔案，並選取後 **[確定]**，則<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法用來在記事本中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="90dba-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](../../../../samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](../../../../samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="90dba-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90dba-119">See also</span></span>
- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="90dba-120">OpenFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="90dba-120">OpenFileDialog component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
