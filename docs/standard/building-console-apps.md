---
title: "在 .NET Framework 中建置主控台應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8bcfa7d8a55cd2754965430db7ea6d2351892658
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="building-console-applications-in-the-net-framework"></a>在 .NET Framework 中建置主控台應用程式
.NET Framework 中的應用程式可以使用 <xref:System.Console?displayProperty=nameWithType> 類別從主控台讀取字元，以及將字元寫入主控台。 來自主控台的資料會從標準輸入資料流讀取，要傳送到主控台的資料會寫入至標準輸出資料流，而傳送給主控台的錯誤資料則會寫入至標準錯誤輸出資料流。 在應用程式啟動時，這些資料流會自動與主控台產生關聯，並且分別表示為 <xref:System.Console.In%2A>、<xref:System.Console.Out%2A> 和 <xref:System.Console.Error%2A> 屬性。  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> 屬性的值是一個 <xref:System.IO.TextReader?displayProperty=nameWithType> 物件，而 <xref:System.Console.Out%2A?displayProperty=nameWithType> 和 <xref:System.Console.Error%2A?displayProperty=nameWithType> 屬性的值則為 <xref:System.IO.TextWriter?displayProperty=nameWithType> 物件。 您可以使這些屬性與不代表主控台的資料流產生關聯，讓您能夠替輸入或輸出將資料流指向不同位置。 例如，您可以將 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.IO.StreamWriter?displayProperty=nameWithType>，這樣會透過 <xref:System.Console.SetOut%2A?displayProperty=nameWithType> 方法封裝 <xref:System.IO.FileStream?displayProperty=nameWithType>，藉此將輸出重新導向至檔案。 <xref:System.Console.In%2A?displayProperty=nameWithType> 和 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性不需要參考相同資料流。  
  
> [!NOTE]
>  如需建置主控台應用程式的詳細資訊 (含 C#、Visual Basic 及 C++ 的範例)，請參閱 <xref:System.Console> 類別的文件。  
  
 因為沒有可以將資訊寫入的主控台，所以如果主控台不存在 (例如在 Windows 架構應用程式中) 的話，將看不到寫入標準輸出資料流的輸出。 將資訊寫入不可存取的主控台不會導致引發例外狀況。  
  
 此外，若要在使用 Visual Studio 開發的 Windows 架構應用程式內啟用主控台來讀取和寫入，請開啟專案的 [屬性] 對話方塊，按一下 [應用程式] 索引標籤，然後將 [應用程式類型] 設定為 [主控台應用程式]。  
  
 主控台應用程式缺乏預設會啟動的訊息幫浦 (Message Pump)。 因此，對 Microsoft Win32 計時器的主控台呼叫可能會失敗。  
  
 **System.Console** 類別具有可以從主控台讀取個別字元或整行的方法。 其他方法會轉換資料和格式字串，並接著將格式化的字串寫到主控台。 如需格式化字串的詳細資訊，請參閱[格式化類型](../../docs/standard/base-types/formatting-types.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Console?displayProperty=nameWithType>  
 [格式化類型](../../docs/standard/base-types/formatting-types.md)
