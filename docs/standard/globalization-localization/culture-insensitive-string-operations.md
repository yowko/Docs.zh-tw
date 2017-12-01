---
title: "不區分文化特性的字串作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dddd46dc5d825738dd9d5038ae573910122953c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="culture-insensitive-string-operations"></a>不區分文化特性的字串作業
如果您建立的應用程式會根據個別文化特性對使用者顯示結果，區分文化特性字串作業將有所助益。 根據預設，區分文化特性的方法會從目前執行緒的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 屬性取得要使用的文化特性。  
  
 請注意，區分文化特性的字串作業並不一定是所要的行為。 若結果應該與文化特性無關，但使用了區分文化特性的作業，可能會造成應用程式程式碼在具有自訂大小寫對應和排序規則的文化特性上失敗。 如需範例，請參閱中的 「 字串比較，使用目前文化特性 」 一節[使用字串的最佳作法](../../../docs/standard/base-types/best-practices-strings.md)發行項。  
  
 字串作業是否應該區分文化特性取決於您的應用程式如何使用結果。 對使用者顯示結果的字串作業，通常都是區分文化特性的。 例如，如果應用程式要在清單方塊中顯示排序過的當地語系化字串清單，應用程式就應該執行區分文化特性的排序。  
  
 用於內部的字串作業的結果，通常都是不區分文化特性的。 一般而言，如果應用程式使用沒有對使用者顯示的檔名、保存性格式或符號資訊，字串作業的結果便不應該因文化特性而有所不同。 例如，如果應用程式進行字串的比較，以判斷該字串是否為可以辨認的 XML 標記，則這項比較就不應是區分文化特性的。 此外，如果安全性決策必須依據字串比較的結果進行，則作業應該不區分文化特性，以確保結果不受 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 的值影響。  
  
 不論您是否要開發含有處理當地語系化和全球化問題之程式碼的應用程式，您應該知道預設情況下會擷取區分文化特性結果的 .NET Framework 方法。 本主題的目的在說明當您的應用程式想要取得不區分文化特性的結果時，使用這些方法的正確方式。  
  
## <a name="see-also"></a>另請參閱  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)
