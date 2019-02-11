---
title: HOW TO：讀取檔案中的文字
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa6787e018b540dbf19b6da3473b699096cc4ae3
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674395"
---
# <a name="how-to-read-text-from-a-file"></a>HOW TO：讀取檔案中的文字
下列範例將示範如何以同步和非同步方式，從使用適用於桌面應用程式的 .NET 之文字檔讀取文字。 在這兩個範例中，當您建立 <xref:System.IO.StreamReader> 類別的執行個體時，會提供檔案的相對路徑或絕對路徑。 
  
> [!NOTE]
> 由於 Windows 執行階段提供不同的資料流類型來讀取和寫入檔案，因此這些程式碼不適用於 Universal Windows (UWP) 應用程式的開發工作。 如需示範如何在 UWP 應用程式中從檔案讀取文字的範例，請參閱[快速入門：讀取和寫入檔案](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))。 如需示範如何在 .NET Framework 資料流和 Windows 執行階段資料流之間進行轉換的範例，請參閱[如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)。  
  
## <a name="example-synchronous-read-in-a-console-app"></a>範例：主控台應用程式中的同步讀取  
下列範例將示範在主控台應用程式內的同步讀取作業。 此範例會使用資料流讀取器開啟文字檔、將內容複製到字串，並將字串輸出至主控台。  
  
> [!IMPORTANT]
> 範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>範例：WPF 應用程式中的非同步讀取 
 下列範例將示範 Windows Presentation Foundation (WPF) 應用程式內的非同步讀取作業。  
  
> [!IMPORTANT]
> 範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [如何：建立目錄清單](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [快速入門：讀取和寫入檔案](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [如何：讀取字串中的字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [如何：將字元寫入字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
