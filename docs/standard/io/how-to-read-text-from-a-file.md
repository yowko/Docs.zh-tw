---
title: 如何：從檔案讀取文字
description: 在本文中，您可以使用適用于傳統型應用程式的 .NET 中的 StreamReader 類別，查看如何以同步或非同步方式從文字檔讀取文字的範例。
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 48b862ff77bf4ace48a5481fe9bedcf354b5654b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725335"
---
# <a name="how-to-read-text-from-a-file"></a>如何：從檔案讀取文字

下列範例將示範如何以同步和非同步方式，從使用適用於桌面應用程式的 .NET 之文字檔讀取文字。 在這兩個範例中，當您建立 <xref:System.IO.StreamReader> 類別的執行個體時，會提供檔案的相對路徑或絕對路徑。
  
> [!NOTE]
> 這些程式碼範例不適用於通用 Windows (UWP) 應用程式，因為 Windows 執行階段提供不同的串流類型來讀取和寫入檔案。 如需顯示如何在 UWP 應用程式中從檔案讀取文字的範例，請參閱 [快速入門：讀取和寫入](/previous-versions/windows/apps/hh758325(v=win.10))檔案。 如需示範如何在 .NET Framework 資料流程和 Windows 執行階段資料流程之間轉換的範例，請參閱 [如何：在 .NET Framework 資料流程和 Windows 執行階段資料流程之間進行轉換](how-to-convert-between-dotnet-streams-and-winrt-streams.md)。  
  
## <a name="example-synchronous-read-in-a-console-app"></a>範例：在主控台應用程式中同步讀取  

下列範例將示範在主控台應用程式內的同步讀取作業。 此範例會使用資料流讀取器開啟文字檔、將內容複製到字串，並將字串輸出至主控台。  
  
> [!IMPORTANT]
> 範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>範例： WPF 應用程式中的非同步讀取

 下列範例將示範 Windows Presentation Foundation (WPF) 應用程式內的非同步讀取作業。  
  
> [!IMPORTANT]
> 範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [非同步檔案 I/O](asynchronous-file-i-o.md)  
- [如何：建立目錄清單](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [快速入門：讀取和寫入檔案](/previous-versions/windows/apps/hh758325(v=win.10))  
- [如何：在 .NET Framework 資料流程和 Windows 執行階段資料流程之間轉換](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [如何：讀取和寫入新建立的資料檔案](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：開啟並附加至記錄檔](how-to-open-and-append-to-a-log-file.md)  
- [如何：將文字寫入檔案](how-to-write-text-to-a-file.md)  
- [如何：從字串讀取字元](how-to-read-characters-from-a-string.md)  
- [如何：將字元寫入字串](how-to-write-characters-to-a-string.md)  
- [檔案和資料流 I/O](index.md)
