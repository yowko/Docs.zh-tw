---
title: "匯入類型程式庫做為組件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM Interop, 公開 COM 元件"
  - "COM Interop, 匯入類型程式庫"
  - "自訂包裝函式"
  - "將 COM 元件公開給 .NET Framework"
  - "匯入類型程式庫"
  - "與 Unmanaged 程式碼的互通, 公開 COM 元件"
  - "與 Unmanaged 程式碼的互通, 匯入類型程式庫"
  - "中繼資料"
  - "類型程式庫"
  - "類型程式庫匯入工具"
  - "類型中繼資料"
  - "TypeLibConverter 類別, 匯入類型程式庫做為組件"
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 匯入類型程式庫做為組件
COM 型別定義通常位於型別程式庫中。  反之，符合 CLS 的編譯器則是在組件中產生型別中繼資料。  這兩種型別資訊的來源有相當大的差異。  這個主題是描述從型別程式庫產生中繼資料的技術。  產生的組件稱為 Interop 組件，其包含的型別資訊可讓 .NET Framework 應用程式使用 COM 型別。  
  
 有兩種方式可以讓此型別資訊可用於應用程式中：  
  
-   使用僅限設計階段的 Interop 組件：以 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，您可以指示編譯器將 Interop 組件的型別資訊內嵌至可執行檔中。  編譯器只會內嵌應用程式使用的型別資訊。  您不一定要隨應用程式一起部署 Interop 組件。  這是建議使用的技巧。  
  
-   部署 Interop 組件：您可以建立 Interop 組件的標準參考。  在這種情況下，Interop 組件必須隨您的應用程式一起部署。  如果您使用此方法，而且並未使用私密 COM 元件，請務必參考要併入 Managed 程式碼之 COM 元件作者所發行的主要 Interop 組件 \(PIA\)。  如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](http://msdn.microsoft.com/zh-tw/b977a8be-59a0-40a0-a806-b11ffba5c080)。  
  
 當使用僅限設計階段的 Interop 組件時，您可以內嵌來自 COM 元件作者所發行的主要 Interop 組件的型別資訊。  然而，您不一定要隨應用程式一起部署主要 Interop 組件。  
  
 使用僅限設計階段 Interop 組件會減少應用程式的大小，因為大部分應用程式都沒有使用 COM 元件的所有功能。  編譯器在內嵌型別資訊時非常有效，如果應用程式只使用 COM 介面的部分方法，則編譯器不會內嵌未使用的方法。  當具有內嵌型別資訊的應用程式與其他此類應用程式互動，或與使用主要 Interop 組件的應用程式互動時，Common Language Runtime 會使用型別相同規則來判斷兩個型別是否使用相同的名稱表示相同的 COM 型別。  您不需要了解這些規則即可使用 COM 物件。  然而，如果對這些規則感興趣，請參閱[類型等價和內嵌 Interop 類型](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md)。  
  
## 產生中繼資料  
 COM 型別程式庫可以是單獨的檔案，副檔名為 .tlb \(例如 Loanlib.tlb\)。  而有些型別程式庫則會嵌入在 .dll 或 .exe 檔案的資源區段中。  型別程式庫資訊的其他來源為 .olb 和 .ocx 檔案。  
  
 找到包含目標 COM 型別實作的型別程式庫後，您可以使用下列選項，產生包含型別中繼資料的 Interop 組件：  
  
-   Visual Studio  
  
     Visual Studio 會自動將型別程式庫中的 COM 型別轉換為組件中的中繼資料。  如需相關說明，請參閱 [HOW TO：將參考加入至型別程式庫](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)和[逐步解說：從 Microsoft Office 組件內嵌類型資訊](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
-   [型別程式庫匯入工具 \(TlbImp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     型別程式庫匯入工具提供命令列選項，可以調整產生的 Interop 檔案的中繼資料 \(Metadata\)、從現有型別程式庫匯入型別，並產生 Interop 組件 \(Assembly\) 和命名空間。  如需相關說明，請參閱 [HOW TO：從型別程式庫產生 Interop 組件](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)。  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=fullName> 類別  
  
     這個類別提供將型別程式庫中的 Coclass 和介面轉換成組件內中繼資料的方法。  它會產生與 Tlbimp.exe 完全相同的中繼資料輸出。  然而，與 Tlbimp.exe 不同，<xref:System.Runtime.InteropServices.TypeLibConverter> 類別可以將記憶體中型別程式庫轉換成中繼資料。  
  
-   自訂包裝函式  
  
     當型別程式庫無法使用或不正確時，另一種選擇就是在 Managed 原始程式碼中建立類別或介面的重複定義。  然後您可以用針對 Runtime 為目標的編譯器編譯這個原始程式碼，以產生組件中的中繼資料。  
  
     若要以手動方式定義 COM 型別，您必須擁有下列項目的存取權：  
  
    -   要定義的 Coclass 和介面的精確描述。  
  
    -   能夠產生適當 .NET Framework 類別定義的編譯器，例如 C\# 編譯器。  
  
    -   型別程式庫轉換為組件的轉換規則知識。  
  
     撰寫自訂包裝函式是進階技術。  如需如何產生自訂包裝函式的詳細資訊，請參閱[自訂標準包裝函式](http://msdn.microsoft.com/zh-tw/c40d089b-6a3c-41b5-a20d-d760c215e49d)。  
  
 如需 COM Interop 匯入處理序的詳細資訊，請參閱[型別程式庫至組件轉換的摘要](http://msdn.microsoft.com/zh-tw/bf3f90c5-4770-4ab8-895c-3ba1055cc958)。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.TypeLibConverter>   
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/zh-tw/bf3f90c5-4770-4ab8-895c-3ba1055cc958)   
 [Tlbimp.exe \(Type Library Importer\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)   
 [Customizing Standard Wrappers](http://msdn.microsoft.com/zh-tw/c40d089b-6a3c-41b5-a20d-d760c215e49d)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/zh-tw/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [編譯 Interop 專案](../../../docs/framework/interop/compiling-an-interop-project.md)   
 [部署 Interop 應用程式](../../../docs/framework/interop/deploying-an-interop-application.md)   
 [如何：將參考加入至類型程式庫](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)   
 [如何：從類型程式庫產生 Interop 組件](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)   
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)