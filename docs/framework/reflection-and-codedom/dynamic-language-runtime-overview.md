---
title: "Dynamic Language Runtime 概觀 | Microsoft Docs"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ea1f9f071d749058450487d25bdff13ca04549
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="dynamic-language-runtime-overview"></a>Dynamic Language Runtime 概觀
「動態語言執行階段」(DLR) 是在 Common Language Runtime (CLR) 中新增一組動態語言服務的執行階段環境。 DLR 可讓您輕鬆地開發動態語言以便在 .NET Framework 上執行，以及將動態功能新增至靜態類型語言。  
  
 動態語言可以在執行階段識別物件的類型，而在靜態類型語言，例如 C# 和 Visual Basic 中 (當您使用 `Option Explicit On` 時)，您必須在設計階段指定物件類型。 動態語言的範例包括 Lisp、Smalltalk、JavaScript、PHP、Ruby、Python、ColdFusion、Lua、Cobra 和 Groovy。  
  
 大部分動態語言為開發人員提供下列優點：  
  
-   能夠使用快速意見反應迴圈 (REPL，或讀取-評估-列印迴圈)。 這可讓您輸入多個陳述式，並立即執行它們來查看結果。  
  
-   支援由上而下開發和更傳統的由下而上開發。 比方說，當您使用由上而下方法時，可以呼叫尚未實作的函式，並在需要時再新增基礎實作。  
  
-   更容易進行重構和程式碼修改，因為您不需要變更整個程式碼的靜態類型宣告。  
  
 動態語言促成了絕佳的指令碼語言。 客戶可以使用具有新命令和功能的動態語言，輕鬆地擴充已建立的應用程式。 動態語言也經常用來建立網站和測試控管、維護伺服器陣列、開發各種公用程式，以及執行資料轉換。  
  
 DLR 的目的是讓動態語言系統能在 .NET Framework 上執行，並提供它們 .NET 互通性。 DLR 將動態物件引入 Visual Studio 2010 中的 C# 和 Visual Basic，以支援這些語言中的動態行為，並啟用其與動態語言的互通。  
  
 DLR 也可協助您建立支援動態作業的程式庫。 比方說，如果您有使用 XML 或 JavaScript 物件標記法 (JSON) 物件的程式庫，您的物件對於使用 DLR 的語言而言，可以作為動態物件。 這可讓程式庫使用者撰寫語法更簡單且更自然的程式碼，來使用物件以及存取物件成員。  
  
 比方說，您可能使用下列程式碼，以 C# 遞增 XML 中的計數器。  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 藉由使用 DLR，您可以改為使用下列程式碼進行相同的作業。  
  
 `scriptobj.Count += 1;`  
  
 就像 CLR，DLR 是 .NET Framework 的一部分，並與 .NET Framework 和 Visual Studio 安裝套件一起提供。 DLR 的開放原始碼版本也可以在 GitHub 的 [IronLanguages/dlr](https://github.com/IronLanguages/dlr) 存放庫上下載。  
  
> [!NOTE]
>  DLR 的開放原始碼版本有 Visual Studio 和 .NET Framework 中包含之 DLR 的所有功能。 它也提供其他支援給語言實作人員。 如需詳細資訊，請參閱 GitHub 的 [IronLanguages/dlr](https://github.com/IronLanguages/dlr) 存放庫上的文件。 
  
 使用 DLR 語言開發的範例包括下列各項：  
  
-   IronPython。 在 [GitHub](https://github.com/IronLanguages/ironpython2) 網站上以開放原始碼軟體形式提供。  
  
-   IronRuby。 以開放原始碼軟體於 [RubyForge](http://go.microsoft.com/fwlink/?LinkId=141044) 網站上提供。  
  
## <a name="primary-dlr-advantages"></a>主要的 DLR 優點  
 DLR 提供下列優點。  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>簡化將動態語言移轉至 .NET Framework  
 DLR 可讓語言實作人員避免建立語彙分析器、剖析器、語意分析器、程式碼產生器以及他們以往都會需要自己建立的其他工具。 若要使用 DLR，語言需要產生*運算式樹狀架構*，它代表樹狀結構中的語言層級程式碼、執行階段 helper 常式，和實作 <xref:System.Dynamic.IDynamicMetaObjectProvider> 介面的選擇性動態物件。 DLR 和 .NET Framework 會自動執行大量的程式碼分析和程式碼產生工作。 這讓語言實作人員能專注於獨特的語言功能。  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>啟用靜態類型語言中的動態功能  
 現有的 .NET Framework 語言，例如 C# 和 Visual Basic，可以建立動態物件，並使用它們搭配靜態類型物件。 例如，C# 和 Visual Basic 可以使用動態物件進行 HTML、文件物件模型 (DOM) 和 .NET 反映。  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>提供 DLR 和 .NET Framework 的未來優點  
 使用 DLR 實作的語言可以受益於未來的 DLR 和 .NET Framework 增強功能。 比方說，如果 .NET Framework 發行已改善記憶體回收行程或更快組件載入的新版本，使用 DLR 實作的語言會立即獲得相同的優點。 如果 DLR 新增例如更佳編譯的最佳化作業，使用 DLR 實作的所有語言效能也會改善。  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>啟用程式庫和物件的共用  
 實作在一種語言中的物件和程式庫可以由其他語言使用。 DLR 也可啟用靜態類型和動態語言之間的交互操作。 例如，C# 可以宣告使用以動態語言所撰寫之程式庫的動態物件。 在此同時，動態語言都可以使用 .NET Framework 的程式庫。  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>提供快速動態分派和叫用  
 DLR 藉由支援進階的多型快取而提供動態作業的快速執行。 DLR 會建立規則，以便將使用物件的作業繫結到必要的執行階段實作，然後再快取這些規則，以避免在對相同物件類型連續執行相同程式碼期間發生耗盡資源的繫結計算。  
  
## <a name="dlr-architecture"></a>DLR 架構  
 下圖顯示動態語言執行階段的架構。  
  
 ![Dynamic Language Runtime 架構概觀](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
DLR 架構  
  
 DLR 新增一組服務給 CLR，以便更妥善支援動態語言。 這些服務包括下列各項：  
  
-   運算式樹狀架構。 DLR 使用運算式樹狀架構來代表語言語意。 基於此目的，DLR 有擴充的 LINQ 運算式樹狀架構，包含控制流程、指派及其他語言模型節點。 如需詳細資訊，請參閱[運算式樹狀架構](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)。  
  
-   呼叫站台快取。 「動態呼叫站台」是程式碼中您用來對動態物件執行像是 `a + b` 或 `a.b()` 等作業的地方。 DLR 會快取 `a` 和 `b` 的特性 (通常是這些物件的類型) 和作業的相關資訊。 如果先前已執行此類作業，DLR 會從快取擷取所有必要資訊以便快速分派。  
  
-   動態物件互通性。 DLR 提供一組類別和介面，代表動態物件和作業，而且可以由語言實作者和動態程式庫的作者所使用。 這些類別和介面包括 <xref:System.Dynamic.IDynamicMetaObjectProvider>、<xref:System.Dynamic.DynamicMetaObject>、<xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject>。  
  
 DLR 使用呼叫站台中的繫結器來進行通訊，不只是與 .NET Framework，也與其他基礎結構和服務通訊，包括 Silverlight 和 COM。 繫結器會封裝語言的語意，並指定如何使用運算式樹狀架構在呼叫站台執行作業。 這樣可讓動態語言和使用 DLR 的靜態類型語言共用程式庫，以及存取 DLR 所支援的所有技術。  
  
## <a name="dlr-documentation"></a>DLR 文件  
 如需如何使用 DLR 開放原始碼版本將動態行為新增至語言的詳細資訊，或如何搭配使用動態語言與 .NET Framework 的詳細資訊，請參閱 GitHub 的 [IronLanguages/dlr](https://github.com/IronLanguages/dlr/tree/master/Docs) 存放庫上的文件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [通用語言執行平台](../../../docs/standard/clr.md)  
 [運算式樹狀結構](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [逐步解說：建立和使用動態物件](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
