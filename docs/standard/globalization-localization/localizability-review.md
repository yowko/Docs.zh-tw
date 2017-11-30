---
title: "可當地語系化檢閱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a>可當地語系化檢閱
當地語系化能力審查是準備發行到全球之應用程式開發工作的中繼步驟。 這個步驟會確認全球化應用程式是否準備好進行當地語系化，以及識別使用者介面中需要特殊處理的任何程式碼或任何方面。 另外還可協助確保當地語系化過程中，不會在應用程式中造成任何功能上的問題。 當地語系化能力審查提出的所有問題都獲得解決之後，您的應用程式就可以開始進行當地語系化。 如果當地語系化能力審查相當徹底，您應該不需要在當地語系化過程期間修改任何原始程式碼。  
  
 當地語系化能力審查包括下列三項檢查：  
  
-   [會實作全球化建議？](#global)  
  
-   [區分文化特性的功能是否正確處理？](#culture)  
  
-   [您已經測試操作國際資料的應用程式嗎？](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>實作全球化建議  
 如果您設計和開發您的應用程式當地語系化，請注意，如果您遵循建議的討論中，而且[全球化](../../../docs/standard/globalization-localization/globalization.md)發行項，則當地語系化能力檢閱將會大量地品質保證傳遞. 否則，在這個階段您應該檢閱並實作的建議[全球化](../../../docs/standard/globalization-localization/globalization.md)，並且修正原始程式碼中造成當地語系化無法順利的錯誤。  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>處理區分文化特性的功能  
 .NET Framework 在一些文化特性差異較大的區域並未提供程式設計方面的支援。 在大部分情況下，您必須撰寫自訂程式碼來處理下列領域：  
  
-   位址。  
  
-   電話號碼。  
  
-   紙張大小。  
  
-   用於長度、粗細、面積、容積和溫度的測量單位。 雖然 .NET Framework 並未提供在測量單位之間進行轉換的內建支援，但是您可以使用 <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> 屬性判斷特定國家或地區是否使用公制，如下列範例所示。  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>測試應用程式  
 在您將應用程式當地語系化之前，應先使用國際版作業系統上的國際資料進行測試。 雖然大部分使用者介面此時並不會當地語系化，但是您將能夠偵測出問題所在，如下所示：  
  
-   無法跨作業系統版本正確還原序列化的序列化資料。  
  
-   未反映目前文化特性慣例的數值資料。 例如，數字可能採用不正確的群組分隔符號、小數點分隔符號或貨幣符號顯示。  
  
-   未反映目前文化特性慣例的日期和時間資料。 例如，表示月份和日期的數字可能以不正確的順序出現、日期分隔符號可能不正確，或是時區資訊可能不正確。  
  
-   找不到資源，因為您尚未識別應用程式的預設文化特性。  
  
-   特定文化特性的字串以異常的順序顯示。  
  
-   傳回未預期結果的字串比較或相等比較。  
  
 如果您已開發應用程式時，所遵照全球化建議、 正確處理區分文化特性的功能識別並解決當地語系化問題所引發在測試期間，您可以繼續到下一個步驟中， [當地語系化](../../../docs/standard/globalization-localization/localization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)  
 [當地語系化](../../../docs/standard/globalization-localization/localization.md)  
 [全球化](../../../docs/standard/globalization-localization/globalization.md)  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
