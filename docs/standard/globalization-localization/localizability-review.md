---
title: "可當地語系化檢閱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "世界性的應用程式，可當地語系化"
  - "應用程式開發 [.NET Framework]，當地語系化"
  - "可當地語系化 [.NET Framework]"
  - "國際應用程式 [.NET Framework]，可當地語系化"
  - "全球化 [.NET Framework]，可當地語系化"
  - "文化特性，可當地語系化"
  - "當地語系化 [.NET Framework]，可當地語系化"
  - "全球化應用程式，可當地語系化"
  - "當地語系化資源"
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 可當地語系化檢閱
可當地語系化檢閱是世界性的應用程式開發的中間步驟。  它會驗證全球化應用程式準備好執行當地語系化，以及識別任何程式碼或需要特殊處理使用者介面的任何方面。  這個步驟也協助確保當地語系化流程將不引入任何功能缺失至您的應用程式中。  當可當地語系化檢閱提出的任何問題解決後，您的應用程式準備好執行當地語系化。  如果可當地語系化檢閱是完整，您不需要在當地語系化程序中修改任何原始程式碼。  
  
 可當地語系化檢閱包括下列三個檢查：  
  
-   [是否實作全球化建議?](#global)  
  
-   [文化特性的功能正確處理?](#culture)  
  
-   [您測試過使用國際資料的應用程式嗎?](#test)  
  
<a name="global"></a>   
## 實作全球化建議  
 如果已設計和開發的應用程式時未當地語系化，和如果您遵循 [全球化](../../../docs/standard/globalization-localization/globalization.md) 文章中討論的建議，可當地語系化檢閱主要是品質保證傳遞。  否則，在這個階段您應該檢閱及實作 [全球化](../../../docs/standard/globalization-localization/globalization.md)的建議，然後在原始程式碼更正防止當地語系化的錯誤。  
  
<a name="culture"></a>   
## 處理區分文化特性的功能  
 .NET Framework 不會提供在文化特性多個變更的區域的方式支援。  在大部分情況下，您必須以處理如下的功能區域撰寫自訂程式碼：  
  
-   位址  
  
-   電話號碼。  
  
-   紙張大小。  
  
-   用於長度、粗細、區域、大小和溫度的測量單位。  雖然 .NET Framework 不會提供內建支援在測量單位之間的轉換，您可以使用 <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=fullName> 屬性判斷特定國家或地區是否使用公制，如下列範例所示。  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## 測試應用程式  
 在您當地語系化應用程式之前，您應該測試它使用作業系統的國際版本的國際資料。  雖然大部分使用者介面此時不會當地語系化，您可以偵測到問題如下所示：  
  
-   無法跨作業系統版本正確的序列化資料。  
  
-   不會反映目前文化特性慣例的數值資料。  例如，數字可能顯示具有不正確的群組分隔符號、小數點分隔符號、貨幣符號。  
  
-   不會反映目前文化特性慣例的日期和時間資料。  例如，表示月份日期，然後可以按錯誤順序出現的數字、日期分隔符號可能不正確或時區資訊可能會不正確。  
  
-   找不到資源，因為您未識別應用程式的預設文化特性。  
  
-   依特定文化特性之例外狀況的順序顯示的字串。  
  
-   傳回未預期的結果的字串比較或比較是否相等。  
  
 如果您遵循全球化建議，正確地開發應用程式、處理區分文化特性的功能、及在測試期間識別和發生當地語系化問題時，您可以繼續下一個步驟中，[當地語系化](../../../docs/standard/globalization-localization/localization.md)。  
  
## 請參閱  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)   
 [當地語系化](../../../docs/standard/globalization-localization/localization.md)   
 [全球化](../../../docs/standard/globalization-localization/globalization.md)   
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)