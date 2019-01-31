---
title: HOW TO：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a006d739b6fa9a31ad238702dd0b2d26254deca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492756"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>HOW TO：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換

適用 Windows 市集應用程式的 .NET Framework 是完整 .NET Framework 的子集。 基於 Windows 市集應用程式的安全性和其他要求，您無法使用整套 .NET Framework API 開啟和讀取檔案。 如需詳細資訊，請參閱[適用於 Windows 市集應用程式的 .NET 概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))。 不過，您可能會想要使用 .NET Framework API 進行其他資料流管理作業。 若要管理這些資料流，您可能會發現需要在 .NET Framework 資料流類型 (例如 <xref:System.IO.MemoryStream> 或 <xref:System.IO.FileStream>) 和 Windows 執行階段資料流 (例如 <xref:Windows.Storage.Streams.IInputStream>、<xref:Windows.Storage.Streams.IOutputStream> 或 <xref:Windows.Storage.Streams.IRandomAccessStream>) 之間轉換。

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) 類別包含可簡化這些轉換的方法。 不過，.NET Framework 和 Windows 執行階段之間有一些基本差異，將會影響使用這些方法的結果。 下面各節將有詳細說明。

## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>從 Windows 執行階段資料流轉換為 .NET Framework 資料流

您可以使用下列其中一種 [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) 方法，從 Windows 執行階段資料流轉換為 .NET Framework 資料流：

[System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx)  
將 Windows 執行階段中的隨機存取資料流轉換成適用於 Windows 市集應用程式的 .NET 子集中的 Managed 資料流。

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx)  
將 Windows 執行階段中的輸出資料流轉換成適用於 Windows 市集應用程式的 .NET 子集中的 Managed 資料流。

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx)  
將 Windows 執行階段中的輸入資料流轉換成適用於 Windows 市集應用程式的 .NET 子集中的 Managed 資料流。

Windows 執行階段提供了可支援唯讀、唯寫或讀寫的資料流類型，這些功能會在您將 Windows 執行階段資料流轉換成 .NET Framework 資料流時保留。 此外，如果您將 Windows 執行階段資料流轉換成 .NET Framework 資料流之後再反向轉換，則會得到原始的 Windows 執行階段執行個體。 最佳作法是使用符合您要轉換之 Windows 執行階段資料流功能的轉換方法。 不過，<xref:Windows.Storage.Streams.IRandomAccessStream> 可讀取和寫入 (它會實作 <xref:Windows.Storage.Streams.IOutputStream> 和 <xref:Windows.Storage.Streams.IInputStream>)，因此您可以使用任何轉換方法，而原始資料流的功能將會保留。 例如，使用 [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) 轉換 <xref:Windows.Storage.Streams.IRandomAccessStream> 不會將轉換後的 .NET Framework 資料流限制為唯讀，該資料流也可以寫入。

### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>若要從 Windows 執行階段隨機存取資料流轉換成 .NET Framework 資料流

- 使用 [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) 方法。

  下列程式碼範例將示範如何提示使用者選取檔案、使用 Windows 執行階段 API 將檔案開啟，然後將檔案轉換成會讀取並輸出至文字區塊的 .NET Framework 資料流。 在這個情境中，您通常會在輸出結果之前，使用 .NET Framework API 管理資料流。

  若要執行這個範例，您必須建立包含名為 `TextBlock1` 的文字區塊及名為  `Button1`的按鈕之 Windows 市集 XAML 應用程式。 按鈕點選事件必須與範例中所顯示的 `button1_Click` 方法相關聯。

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]

## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>從 .NET Framework 資料流轉換為 Windows 執行階段資料流

您可以使用下列其中一種 [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) 方法，從 .NET Framework 資料流轉換為 Windows 執行階段資料流：

[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) 將適用於 Windows 市集應用程式的 .NET 子集中的受控資料流轉換成 Windows 執行階段中的輸入資料流。

[System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) 將適用於 Windows 市集應用程式的 .NET 子集中的受控資料流轉換成 Windows 執行階段中的輸出資料流。

[AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) 將適用於 Windows 市集應用程式的 .NET 子集中的受控資料流轉換成可在 Windows 執行階段中用於讀取或寫入的隨機存取資料流。

當您將 .NET Framework 資料流轉換成 Windows 執行階段資料流時，轉換後資料流的功能將取決於原始資料流。 例如，如果原始資料流同時支援讀取和寫入，而且您呼叫 [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) 來轉換資料流，則傳回型別將會是 `IRandomAccessStream`，它會實作 `IInputStream` 和 `IOutputStream` 並支援讀取和寫入。

.NET Framework 資料流不支援複製，即使是在轉換之後也一樣。 這表示，如果您將 .NET Framework 資料流轉換成 Windows 執行階段資料流，並呼叫 <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> 或 <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A> (它會直接呼叫 <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> 或呼叫 <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>)，則例外狀況將會發生。

### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>若要從 .NET Framework 資料流轉換成 Windows 執行階段隨機存取資料流

- 使用 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) 方法，如以下範例所示：

  > [!IMPORTANT]
  > 確定您使用的 .NET Framework 資料流支援搜尋，或將它複製到支援搜尋的資料流。 您可以使用 <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> 屬性來判斷。

  若要執行這個範例，您必須建立以 .NET Framework 4.5.1 為目標且包含名為 `TextBlock2` 的文字區塊和名為 `Button2`的按鈕之 Windows 市集 XAML 應用程式。 按鈕點選事件必須與這個範例中所顯示的 `button2_Click` 方法相關聯。

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]

## <a name="see-also"></a>另請參閱

- [快速入門：讀取和寫入檔案 (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)
- [適用於 Windows 市集應用程式的 .NET 概觀](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)
- [適用於 Windows 市集應用程式的 .NET - 所支援的應用程式開發介面](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)
