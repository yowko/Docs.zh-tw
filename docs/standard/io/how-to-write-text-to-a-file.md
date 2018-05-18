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
ms.openlocfilehash: 13fa71487f143b1054cd2014fa74a1c7245ab31b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-text-to-a-file"></a>如何：將文字寫入檔案
本主題示範可針對 .NET Framework 應用程式或 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，將文字寫入至檔案的幾種不同方式。 通常會使用下列類別和方法，將文字寫入至檔案：  
  
-   <xref:System.IO.StreamWriter> - 包含同步 (<xref:System.IO.StreamWriter.Write%2A> 或 <xref:System.IO.TextWriter.WriteLine%2A>) 或非同步 (<xref:System.IO.StreamWriter.WriteAsync%2A> 和 <xref:System.IO.StreamWriter.WriteLineAsync%2A>) 寫入至檔案的方法。  
  
-   <xref:System.IO.File> - 可搭配 .NET Framework 應用程式使用。 所提供的靜態方法可將文字寫入至檔案 (例如 <xref:System.IO.File.WriteAllLines%2A> 和 <xref:System.IO.File.WriteAllText%2A>)，或將文字附加至檔案 (<xref:System.IO.File.AppendAllLines%2A>、 <xref:System.IO.File.AppendAllText%2A> 或 <xref:System.IO.File.AppendText%2A>)。  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - 可搭配 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式使用。 所包含的非同步方法可將文字寫入至檔案 ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) 或 [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx))，或將文字附加至檔案 ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) 或 [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx))。  

- <xref:System.IO.Path> - 要用於含有檔案或目錄路徑資訊的字串。 它包含 <xref:System.IO.Path.Combine%2A> 方法，可允許使用字串的串連來建置檔案或目錄路徑。


 範例已經過簡化，以便專注於正在執行的工作。 因此，這些範例會執行最少的錯誤檢查和例外狀況處理 (如果有)。 真實世界應用程式通常會提供更強大的錯誤檢查和例外狀況處理。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以同步方式一次一行將文字寫入至新檔案。 新的文字檔會儲存到使用者的 [我的文件] 資料夾。 由於 <xref:System.IO.StreamWriter> 物件是在 `using` 陳述式中宣告及具現化，因此會叫用 <xref:System.IO.StreamWriter.Dispose%2A> 方法，自動清除並關閉資料流。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，將文字附加至現有的檔案。 它會使用來自上一個範例的相同文字檔。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以非同步方式將文字寫入至新檔案。 若要叫用 <xref:System.IO.StreamWriter.WriteAsync%2A> 方法，必須在 `async` 方法中呼叫此方法。 新的文字檔會儲存到使用者的 [我的文件] 資料夾。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.IO.File> 類別，將文字寫入至新檔案，並將新的文字行附加至相同的檔案。 <xref:System.IO.File.WriteAllText%2A> 和 <xref:System.IO.File.AppendAllLines%2A> 方法會自動開啟和關閉檔案。 如果提供給 <xref:System.IO.File.WriteAllText%2A> 方法的路徑已經存在，則會覆寫該檔案。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>範例  
 下面範例示範如何以非同步方式，將使用者輸入寫入至 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中的文字檔。 基於安全考量，從 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式開啟檔案時，通常會需要使用 [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) 控制項。 在這個範例中， `FileOpenPicker` 已篩選為顯示文字檔。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [操作說明：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [操作說明：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [檔案和資料流 I/O](../../../docs/standard/io/index.md)
