---
title: 如何：將文字寫入檔案
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c637d9842c05f47bfcaa0431dd2f9f1ee29cc09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50181234"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="2c29b-102">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="2c29b-102">How to: Write Text to a File</span></span>
<span data-ttu-id="2c29b-103">本主題示範可針對 .NET Framework 應用程式或 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，將文字寫入至檔案的幾種不同方式。</span><span class="sxs-lookup"><span data-stu-id="2c29b-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="2c29b-104">通常會使用下列類別和方法，將文字寫入至檔案：</span><span class="sxs-lookup"><span data-stu-id="2c29b-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="2c29b-105"><xref:System.IO.StreamWriter> - 包含同步 (<xref:System.IO.StreamWriter.Write%2A> 或 <xref:System.IO.TextWriter.WriteLine%2A>) 或非同步 (<xref:System.IO.StreamWriter.WriteAsync%2A> 和 <xref:System.IO.StreamWriter.WriteLineAsync%2A>) 寫入至檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="2c29b-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="2c29b-106"><xref:System.IO.File> - 可搭配 .NET Framework 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="2c29b-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="2c29b-107">所提供的靜態方法可將文字寫入至檔案 (例如 <xref:System.IO.File.WriteAllLines%2A> 和 <xref:System.IO.File.WriteAllText%2A>)，或將文字附加至檔案 (<xref:System.IO.File.AppendAllLines%2A>、 <xref:System.IO.File.AppendAllText%2A> 或 <xref:System.IO.File.AppendText%2A>)。</span><span class="sxs-lookup"><span data-stu-id="2c29b-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="2c29b-108"><xref:Windows.Storage.FileIO> - 可搭配 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="2c29b-108"><xref:Windows.Storage.FileIO> - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="2c29b-109">它包含非同步方法，可將文字寫入至檔案 (例如 <xref:Windows.Storage.FileIO.WriteLinesAsync%2A> 或 <xref:Windows.Storage.FileIO.WriteTextAsync%2A>)，或將文字附加至檔案 (<xref:Windows.Storage.FileIO.AppendLinesAsync%2A> 或 <xref:Windows.Storage.FileIO.AppendTextAsync%2A>)。</span><span class="sxs-lookup"><span data-stu-id="2c29b-109">It contains asynchronous methods to write text to a file (<xref:Windows.Storage.FileIO.WriteLinesAsync%2A> or <xref:Windows.Storage.FileIO.WriteTextAsync%2A>) or to append text to a file (<xref:Windows.Storage.FileIO.AppendLinesAsync%2A> or <xref:Windows.Storage.FileIO.AppendTextAsync%2A>).</span></span>  

- <span data-ttu-id="2c29b-110"><xref:System.IO.Path> - 要用於含有檔案或目錄路徑資訊的字串。</span><span class="sxs-lookup"><span data-stu-id="2c29b-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="2c29b-111">它包含 <xref:System.IO.Path.Combine%2A> 方法，可允許使用字串的串連來建置檔案或目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="2c29b-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="2c29b-112">範例已經過簡化，以便專注於正在執行的工作。</span><span class="sxs-lookup"><span data-stu-id="2c29b-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="2c29b-113">因此，這些範例會執行最少的錯誤檢查和例外狀況處理 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="2c29b-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="2c29b-114">真實世界應用程式通常會提供更強大的錯誤檢查和例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="2c29b-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c29b-115">範例</span><span class="sxs-lookup"><span data-stu-id="2c29b-115">Example</span></span>  
 <span data-ttu-id="2c29b-116">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以同步方式一次一行將文字寫入至新檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="2c29b-117">新的文字檔會儲存到使用者的 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c29b-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="2c29b-118">由於 <xref:System.IO.StreamWriter> 物件是在 `using` 陳述式中宣告及具現化，因此會叫用 <xref:System.IO.StreamWriter.Dispose%2A> 方法，自動清除並關閉資料流。</span><span class="sxs-lookup"><span data-stu-id="2c29b-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="2c29b-119">範例</span><span class="sxs-lookup"><span data-stu-id="2c29b-119">Example</span></span>  
 <span data-ttu-id="2c29b-120">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，將文字附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="2c29b-121">它會使用來自上一個範例的相同文字檔。</span><span class="sxs-lookup"><span data-stu-id="2c29b-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="2c29b-122">範例</span><span class="sxs-lookup"><span data-stu-id="2c29b-122">Example</span></span>  
 <span data-ttu-id="2c29b-123">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以非同步方式將文字寫入至新檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="2c29b-124">若要叫用 <xref:System.IO.StreamWriter.WriteAsync%2A> 方法，必須在 `async` 方法中呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="2c29b-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="2c29b-125">新的文字檔會儲存到使用者的 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c29b-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="2c29b-126">範例</span><span class="sxs-lookup"><span data-stu-id="2c29b-126">Example</span></span>  
 <span data-ttu-id="2c29b-127">下列範例示範如何使用 <xref:System.IO.File> 類別，將文字寫入至新檔案，並將新的文字行附加至相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="2c29b-128"><xref:System.IO.File.WriteAllText%2A> 和 <xref:System.IO.File.AppendAllLines%2A> 方法會自動開啟和關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="2c29b-129">如果提供給 <xref:System.IO.File.WriteAllText%2A> 方法的路徑已經存在，則會覆寫該檔案。</span><span class="sxs-lookup"><span data-stu-id="2c29b-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="2c29b-130">範例</span><span class="sxs-lookup"><span data-stu-id="2c29b-130">Example</span></span>  
 <span data-ttu-id="2c29b-131">下面範例示範如何以非同步方式，將使用者輸入寫入至 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中的文字檔。</span><span class="sxs-lookup"><span data-stu-id="2c29b-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="2c29b-132">基於安全考量，從 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式開啟檔案時，通常會需要使用 <xref:Windows.Storage.Pickers.FileOpenPicker> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2c29b-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a <xref:Windows.Storage.Pickers.FileOpenPicker> control.</span></span> <span data-ttu-id="2c29b-133">在這個範例中， `FileOpenPicker` 已篩選為顯示文字檔。</span><span class="sxs-lookup"><span data-stu-id="2c29b-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a><span data-ttu-id="2c29b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c29b-134">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.Path>  
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="2c29b-135">操作說明：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="2c29b-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="2c29b-136">操作說明：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="2c29b-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="2c29b-137">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="2c29b-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="2c29b-138">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="2c29b-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="2c29b-139">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="2c29b-139">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
