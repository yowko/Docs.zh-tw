---
title: .NET 原生 App 中的執行階段例外狀況
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 3132e2c9502c91cbfa0b120f664fd0c6f99a2663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128150"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>.NET 原生 App 中的執行階段例外狀況
因為偵錯和發行組態完全不同，所以請務必在目標平台上測試通用 Windows 平台 App 的發行組建。 根據預設，偵錯組態會使用 .NET 核心執行階段來編譯 App，但此發行組態會使用 .NET 原生將 App 編譯為原生程式碼。  
  
> [!IMPORTANT]
> 如需處理您在測試應用程式發行版本時可能會遇到的[MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)和[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)例外狀況的相關資訊，請參閱  
  
## <a name="debug-and-release-builds"></a>偵錯與發行組建  
 當偵錯組建針對 .NET 核心執行階段執行時，它尚未被編譯為原生程式碼。 這使得此執行階段平常提供的所有服務可用於您的 App。  
  
 相反地，發行組建會編譯為其目標平台的原生程式碼、移除大部分外部執行階段和程式庫的相依性，以及徹底最佳化程式碼，以追求最大效能。  
  
 當您偵錯使用 .NET 原生編譯的發行組建：  
  
- 您會使用不同於一般 .NET 偵錯工具的 .NET 原生偵錯引擎。  
  
- 會盡可能減少可執行檔的大小。 .NET 原生降低可執行檔大小的其中一種方式，是大幅修剪執行階段例外狀況訊息，這也是在 [Runtime exception messages](#Messages) 一節中更詳細討論的主題。  
  
- 您的程式碼已徹底最佳化。 這代表會盡可能使用內嵌。 （內嵌會將程式碼從外部常式移至呼叫常式）。  .NET Native 提供特製化執行時間並實作用中內嵌的事實，會影響在進行偵錯工具時所顯示的呼叫堆疊。  如需詳細資訊，請參閱 [Runtime call stack](#CallStack) 一節。  
  
> [!NOTE]
> 您可以控制偵錯和發行組建是否以 .NET 原生工具鏈編譯，方法是選取或取消選取 [使用 .NET 原生工具鏈編譯] 方塊。   不過請注意，Windows 市集一律會編譯 App 的 .NET 原生工具鏈生產環境版本。  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Runtime exception messages  
 為了將應用程式可執行檔大小降到最低，.NET 原生不包含例外狀況訊息的完整文字。 如此一來，在發行組建中擲回的執行階段例外狀況，可能無法顯示完整的例外狀況訊息文字。 相反地，此文字可能會包含子字串，以及應遵循的詳細資訊連結。 例如，例外狀況資訊可能會如下所示：  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 如果您需要完整的例外狀況訊息，請改為執行偵錯組建。 例如，來自發行組建的前一筆例外狀況資訊可能會在偵錯組建中出現，如下所示：  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Runtime call stack  
 因為內嵌和其他最佳化的關係，由 .NET 原生工具鏈結編譯之 App 所顯示的呼叫堆疊，可能也無法幫助您清楚識別執行階段例外狀況的路徑。  
  
 若要取得完整的堆疊，請改為執行偵錯組建。  
  
## <a name="see-also"></a>請參閱

- [.NET Native Windows 通用應用程式的偵錯工具](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [使用者入門](getting-started-with-net-native.md)
