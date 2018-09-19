---
title: 擴充方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bfc2e6def94d0830df4a4cdf738cdeef106de9f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323229"
---
# <a name="extension-methods"></a>擴充方法
擴充方法是允許使用執行個體方法呼叫語法來呼叫靜態方法的語言功能。 這些方法必須接受至少一個參數，表示要對方法的執行個體。  
  
 定義這類的擴充方法的類別稱為 「 贊助商 」 類別，它必須宣告為靜態。 若要使用擴充方法，其中必須匯入定義 「 贊助商 」 類別的命名空間。  
  
 **X AVOID** frivolously 特別是在不屬於您的型別上定義擴充方法。  
  
 如果您擁有類型的原始程式碼，請考慮改為使用一般的執行個體方法。 如果不屬於您，而且您想要新增的方法，要非常小心。 自由使用擴充方法有可能會想堆 Api，都不會有這些方法的類型。  
  
 **✓ CONSIDER** 任何下列案例中使用擴充方法：  
  
-   若要提供協助程式功能如果說功能相關的介面，每個實作都可以撰寫方面的核心介面。 這是因為具象實作否則無法指派給介面。 例如，`LINQ to Objects`運算子時，會實作為擴充方法上，所有<xref:System.Collections.Generic.IEnumerable%601>型別。 因此，任何`IEnumerable<>`實作是自動啟用 LINQ。  
  
-   當執行個體方法會產生某種類型的相依性，但這類相依性會中斷相依性管理規則。 比方說，從相依性<xref:System.String>要<xref:System.Uri?displayProperty=nameWithType>不可能需要這樣做，，因此`String.ToUri()`傳回的執行個體方法`System.Uri`會從相依性管理的觀點而言錯誤的設計。 靜態擴充方法`Uri.ToUri(this string str)`傳回`System.Uri`會是更好的設計。  
  
 **X AVOID** 上定義的擴充方法 <xref:System.Object?displayProperty=nameWithType>。  
  
 VB 使用者將無法使用擴充方法語法的物件參考上呼叫這類方法。 VB 不支援呼叫這類方法，因為，在 VB 中，宣告為參考，為物件會強制所有的方法引動過程上才會晚期繫結 （名為的實際成員在執行階段決定），而繫結到擴充方法在編譯時間 （早期決定繫結）。  
  
 請注意指導方針適用於相同的繫結行為所在的其他語言，或不支援的擴充方法。  
  
 **X DO NOT** 擴充方法放在相同的命名空間擴充的型別，除非它是用於將方法加入至介面或相依性管理。  
  
 **X AVOID** 定義兩個或多個使用相同的簽章的擴充方法，即使它們是不同的命名空間中。  
  
 **✓ CONSIDER** 如果類型是介面，並擴充方法的用意是要用於大部分或所有的情況下，擴充的型別相同的命名空間中定義的擴充方法。  
  
 **X DO NOT** 定義實作一項功能通常會與其他功能相關聯的命名空間中的擴充方法。 相反地，在其所屬的功能與相關聯的命名空間中定義它們。  
  
 **X AVOID** 泛型命名的命名空間專門用來擴充方法 (例如，"Extensions")。 使用描述性名稱 （例如，「 路由 」） 改為。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
