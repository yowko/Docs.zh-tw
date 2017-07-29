---
title: "Dynamic Language Runtime 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DLR"
  - "Dynamic Language Runtime"
  - "IronPython"
  - "IronRuby"
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# Dynamic Language Runtime 概觀
*Dynamic Language Runtime* \(DLR\) 是在 Common Language Runtime \(CLR\) 中加入了一組動態語言服務的執行階段環境。  DLR 讓開發在 .NET Framework 上執行的動態語言以及將動態功能加入靜態型別語言變得更為容易。  
  
 動態語言可以在執行階段識別物件的型別，但是在 C\# 和 Visual Basic \(使用 `Option Explicit On` 時\) 等靜態型別語言中，就必須於設計階段指定物件型別。  例如，Lisp、Smalltalk、JavaScript、PHP、Ruby、Python、ColdFusion、Lua、Cobra 和 Groovy 都是動態語言。  
  
 大部分動態語言可以為開發人員提供下列好處：  
  
-   能夠很快完成一個回應循環 \(REPL，即讀取、評估、列印循環\)。  這樣您就可以輸入多個陳述式，並立即執行看到結果。  
  
-   同時支援由上而下的程式開發以及較傳統的由下而上的程式開發。  例如，當您使用由上而下的方式時，可以呼叫尚未實作的函式，然後在需要時才加入基礎實作。  
  
-   更容易進行重構和修改程式碼，因為您不必變更整個程式碼中的靜態型別宣告。  
  
 動態語言可以產生非常好的指令碼語言。  客戶可以輕鬆地搭配新命令和功能，擴充使用動態語言建立的應用程式。  動態語言也經常用於建立網站和測試控管、維護伺服器陣列、開發各種公用程式，以及執行資料轉換。  
  
 DLR 的目的是讓動態語言系統能夠在 .NET Framework 上執行，並為它們提供 .NET 互通性。  DLR 在 Visual Studio 2010 中的 C\# 和 Visual Basic 中加入了動態物件，以便在這些語言中支援動態行為，並啟用與動態語言的互通性。  
  
 DLR 也可以協助您建立支援動態作業的程式庫。  例如，如果您具有使用 XML 或 JavaScript Object Notation \(JSON\) 物件的程式庫，這些物件在使用 DLR 的語言中就可以當作動態物件使用。  如此一來，程式庫使用者就可以撰寫語法較簡單且更自然的程式碼，來操作物件和存取物件成員。  
  
 原本用來遞增 XML 計數器的 C\# 程式碼可能如下所示。  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 若使用 DLR，您可以改用下列程式碼進行同樣的作業。  
  
 `scriptobj.Count += 1;`  
  
 正如 CLR，DLR 也是 .NET Framework 的一部分，同樣隨附於 .NET Framework 及 Visual Studio 安裝套件。  DLR 的開放原始碼版本也可以在網站 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) 下載。  
  
> [!NOTE]
>  DLR 的開放原始碼版本不但具有 Visual Studio 及 .NET Framework 隨附之 DLR 的所有功能，  而且還為語言實作人員 \(Language Implementer\) 提供額外支援。  如需詳細資訊，請參閱在網站上的 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) 文件。  
  
 使用 DLR 開發的語言範例包括下列各項：  
  
-   IronPython，  可用性如同來自 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141040) 網站的開放原始碼軟體。  
  
-   IronRuby，  可用性如同來自 [RubyForge](http://go.microsoft.com/fwlink/?LinkId=141044) 網站的開放原始碼軟體。  
  
## DLR 的主要優點  
 DLR 提供下列優勢：  
  
### 簡化將動態語言移植到 .NET Framework 的工作  
 DLR 讓語言實作人員可以免去傳統上原本必須建立語彙分析器、剖析器、語意分析器、程式碼產生器及其他工具的工作。  若要使用 DLR，語言就必須產生「*運算式樹狀架構*」\(Expression Tree\) \(即以樹形結構表示語言層級程式碼\)、執行階段 Helper 常式，以及實作 <xref:System.Dynamic.IDynamicMetaObjectProvider> 介面的動態物件 \(選擇性\)。  DLR 和 .NET Framework 可以將許多程式碼分析及程式碼產生工作自動化，  讓語言實作人員可以專注於獨特的語言功能。  
  
### 在靜態型別語言中啟用動態功能  
 現有 .NET Framework 語言如 C\# 和 Visual Basic 等都可以建立動態物件，並將這些物件與靜態型別物件一起使用。  例如，C\# 和 Visual Basic 可以為 HTML、文件物件模型 \(DOM\) 及 .NET 反映使用動態物件。  
  
### 提供未來可見的 DLR 與 .NET Framework 效益  
 使用 DLR 實作的語言會因為未來 DLR 和 .NET Framework 的改進而受惠。  例如，如果新版 .NET Framework 改良了記憶體回收行程或加快組件載入時間，使用 DLR 實作的語言就能立即獲得同樣的好處。  如果 DLR 加入像是提高編譯效能這類最佳化，那麼所有使用 DLR 實作的語言效能也會跟著提升。  
  
### 啟用程式庫與物件的共用功能  
 以某個語言實作的物件和程式庫可以由其他語言使用。  DLR 也可以啟用靜態型別語言與動態語言之間的互通性。  例如，C\# 可以宣告會使用以動態語言所撰寫之程式庫的動態物件。  同時，動態語言也可以使用 .NET Framework 的程式庫。  
  
### 提供快速動態分派與引動過程  
 DLR 支援進階多型快取，讓動態作業可以快速執行。  DLR 會建立規定應將使用物件之作業繫結至必要執行階段實作的規則，然後快取這些規則，避免在對相同物件型別連續執行相同程式碼時，進行耗盡資源的繫結運算。  
  
## DLR 架構  
 下圖顯示 Dynamic Language Runtime 的架構。  
  
 ![Dynamic Language Runtime 架構概觀](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR\_ArchOverview")  
DLR 架構  
  
 DLR 會將一組服務加入至 CLR，為動態語言提供更佳的支援。  這些服務包括：  
  
-   運算式樹狀架構：  DLR 會使用運算式樹狀架構來表示語言的語意。  因此，DLR 擴充了 LINQ 運算式樹狀架構，以便包含控制流程、指派及其他語言模型節點。  如需詳細資訊，請參閱[運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)。  
  
-   呼叫位置快取：  「*動態呼叫位置*」\(Dynamic Call Site\) 是您在程式碼中對動態物件執行像是 `a + b` 或 `a.b()` 等作業的地方。  DLR 會快取 `a` 和 `b` 的特性 \(通常是這些物件的型別\) 以及該作業的相關資訊。  如果之前曾經執行這樣的作業，DLR 就會從快取中擷取所有必要的資訊來加速分派。  
  
-   動態物件互通性：  DLR 會提供一組表示動態物件及作業的類別和介面，動態程式庫的語言實作人員和撰寫人員都可以使用。  這些類別和介面包括 <xref:System.Dynamic.IDynamicMetaObjectProvider>、<xref:System.Dynamic.DynamicMetaObject>、<xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject>。  
  
 DLR 會在呼叫位置中使用繫結器，不僅與 .NET Framework 通訊，也會與其他基礎結構和服務 \(包括 Silverlight 和 COM\) 通訊。  繫結器會使用運算式樹狀架構，封裝語言的語意並指定呼叫位置中作業的執行方式。  如此一來，使用 DLR 的動態及靜態型別語言即可共用程式庫，並存取 DLR 支援的所有技術。  
  
## DLR 文件  
 如需如何使用 DLR 開放原始碼版本將動態行為加入語言，或如何搭配使用動態語言與 .NET Framework 的詳細資訊，請參閱 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) 網站 \(英文\) 上的文件。  
  
## 請參閱  
 <xref:System.Dynamic.ExpandoObject>   
 <xref:System.Dynamic.DynamicObject>   
 [Common Language Runtime](../../../docs/standard/clr.md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：建立和使用動態物件](../Topic/Walkthrough:%20Creating%20and%20Using%20Dynamic%20Objects%20\(C%23%20and%20Visual%20Basic\).md)