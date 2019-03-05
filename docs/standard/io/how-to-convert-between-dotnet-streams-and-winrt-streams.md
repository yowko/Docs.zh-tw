---
title: 作法：在 .NET Framework 資料流及 Windows 執行階段資料流之間轉換 (僅限 Windows)
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cf5b621be7532239b67bfe970302f27eca3ea2a
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835131"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>作法：在 .NET Framework 資料流及 Windows 執行階段資料流之間轉換 (僅限 Windows)

.NET Framework for UWP 應用程式是完整 .NET Framework 的子集。 由於 UWP 應用程式的安全性和其他要求，您無法使用整套 .NET Framework API 開啟和讀取檔案。 如需詳細資訊，請參閱 [.NET for UWP 應用程式概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))。 不過，您可能會想要使用 .NET Framework API 進行其他資料流管理作業。 若要管理這些資料流，您可以在 .NET Framework 資料流類型 (例如 <xref:System.IO.MemoryStream> 或 <xref:System.IO.FileStream>) 和 Windows 執行階段資料流 (例如 <xref:Windows.Storage.Streams.IInputStream>、<xref:Windows.Storage.Streams.IOutputStream> 或 <xref:Windows.Storage.Streams.IRandomAccessStream>) 之間轉換。

<xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> 類別包含可簡化這些轉換的方法。 不過，.NET Framework 與 Windows 執行階段資料流之間的基本差異將會影響使用這些方法的結果，下列各節會加以說明：

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>從 Windows 執行階段轉換為 .NET Framework 資料流
若要從 Windows 執行階段資料流轉換為 .NET Framework 資料流，請使用下列其中一個 <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> 方法：

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> 會將 Windows 執行階段中的隨機存取資料流轉換成 .NET 中適用於 UWP 應用程式的受控資料流。
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType> 會將 Windows 執行階段中的輸出資料流轉換成 .NET 中適用於 UWP 應用程式的受控資料流。
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> 會將 Windows 執行階段中的輸入資料流轉換成 .NET 中適用於 UWP 應用程式的受控資料流。

Windows 執行階段提供支援唯讀、唯寫或讀寫的資料流類型。 當您將 Windows 執行階段資料流轉換為.NET Framework 資料流時，這些功能將會保留。 此外，如果您將 Windows 執行階段資料流轉換成 .NET Framework 資料流之後再反向轉換，則會得到原始的 Windows 執行階段執行個體。 

最佳作法是使用符合所要要轉換 Windows 執行階段資料流功能的轉換方法。 不過，因為 <xref:Windows.Storage.Streams.IRandomAccessStream> 可讀取和寫入 (它會同時實作 <xref:Windows.Storage.Streams.IOutputStream> 和 <xref:Windows.Storage.Streams.IInputStream>)，所以轉換方法會保留原始資料流的功能。 例如，使用 <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> 轉換 <xref:Windows.Storage.Streams.IRandomAccessStream> 不會將轉換後的 .NET Framework 資料流限制為唯讀。 它也可寫入。

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>範例：將 Windows 執行階段隨機存取轉換為 .NET Framework 資料流
若要從 Windows 執行階段隨機存取資料流轉換成 .NET Framework 資料流，請使用 <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> 方法。

下列程式碼範例會提示您選取一個檔案、使用 Windows 執行階段 API 將其開啟，然後將其轉換為 .NET Framework 資料流。 它會讀取資料流，並將其輸出至文字區塊。 您通常會在輸出結果之前，使用 .NET Framework API 管理資料流。

若要執行這個範例，請建立一個 UWP XAML 應用程式，其中包含名為 `TextBlock1` 的文字區塊及名為 `Button1` 的按鈕。 將按鈕點選事件與範例中所顯示的 `button1_Click` 方法建立關聯。

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>從 .NET Framework 轉換為 Windows 執行階段資料流
若要從 .NET Framework 資料流轉換為 Windows 執行階段資料流，請使用下列其中一個 <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> 方法：

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> 會將 .NET 中適用於 UWP 應用程式的受控資料流轉換成 Windows 執行階段中的輸入資料流。
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> 會將 .NET 中適用於 UWP 應用程式的受控資料流轉換成 Windows 執行階段中的輸出資料流。
  
- [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) 會將 .NET for UWP 應用程式中的受控資料流轉換為 Windows 執行階段可用於讀取或寫入的隨機存取資料流。

當您將 .NET Framework 資料流轉換成 Windows 執行階段資料流時，轉換後資料流的功能取決於原始資料流。 例如，如果原始資料流同時支援讀取和寫入，而且您呼叫 <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> 來轉換資料流，則傳回的類型為 `IRandomAccessStream`。 `IRandomAccessStream` 會實作 `IInputStream` 和 `IOutputStream`，並支援讀取和寫入。

.NET Framework 資料流不支援複製，即使是在轉換之後也一樣。 如果您將 .NET Framework 資料流轉換為 Windows 執行階段資料流，並呼叫 <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> 或 <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A> (它會呼叫 <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>)，或者您直接呼叫 <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>，則例外狀況將會發生。

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>範例：將 .NET Framework 轉換為 Windows 執行階段隨機存取資料流

若要從 .NET Framework 資料流轉換為 Windows 執行階段隨機存取資料流，請使用 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) 方法，如下列範例所示：

> [!IMPORTANT]
> 確定您使用的 .NET Framework 資料流支援搜尋，或將它複製到支援搜尋的資料流。 您可以使用 <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> 屬性來判斷。

若要執行這個範例，請建立將 .NET Framework 4.5.1 設為目標的 UWP XAML 應用程式，其中包含名為 `TextBlock2` 的文字區塊和名為 `Button2` 的按鈕。 將按鈕點選事件與範例中所顯示的 `button2_Click` 方法建立關聯。

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>另請參閱

- [快速入門：讀取和寫入檔案 (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [適用於 Windows 市集應用程式的 .NET 概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [適用於 Windows 市集應用程式的 .NET 應用程式開發介面](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
