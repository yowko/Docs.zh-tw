---
title: 擴充方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15d36cc2d3073c9f695de81407ecabcd5e3bba30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="extension-methods"></a>擴充方法
擴充方法是讓靜態方法，以使用執行個體方法的呼叫語法來呼叫的語言功能。 這些方法必須使用至少一個參數，表示要對方法的執行個體。  
  
 定義這類的擴充方法的類別稱為 「 贊助者 」 類別，它必須宣告為靜態。 若要使用的擴充方法，一個必須匯入定義贊助者類別的命名空間。  
  
 **請避免 x** frivolously 特別是在不屬於您的型別上定義擴充方法。  
  
 如果您擁有類型的原始程式碼，請考慮改為使用一般的執行個體方法。 如果您並不擁有，而且您想要加入的方法，要非常小心。 盡量使用的擴充方法都有可能會想堆過去並非設計來將這些方法之型別的 Api。  
  
 **✓ 考慮**任何下列案例中使用擴充方法：  
  
-   若要提供 helper 可以核心介面來撰寫功能適用於每個實作的介面時，如果說功能。 這是因為介面否則無法指定具象實作。 例如，`LINQ to Objects`運算子當做擴充方法實作所有<xref:System.Collections.Generic.IEnumerable%601>型別。 因此，任何`IEnumerable<>`實作是自動具備 LINQ 功能。  
  
-   當執行個體方法會導致相依於某些型別，但是這類相依性會中斷相依性管理規則。 相依性，例如，在從<xref:System.String>至<xref:System.Uri?displayProperty=nameWithType>可能不是恰當的，因此`String.ToUri()`傳回的執行個體方法`System.Uri`就是相依性管理的觀點設計錯誤。 靜態之所以`Uri.ToUri(this string str)`傳回`System.Uri`更好的設計。  
  
 **請避免 x**上定義的擴充方法<xref:System.Object?displayProperty=nameWithType>。  
  
 VB 使用者將無法使用擴充方法語法的物件參考上呼叫這類方法。 VB 不支援呼叫這類方法，因為在 VB 中，宣告參考，因為物件會強制所有的方法引動過程上是晚期繫結 （名為實際的成員在執行階段決定），而繫結至擴充方法在編譯時期 （及早決定繫結）。  
  
 請注意在相同的繫結行為是存在，或是不支援擴充方法，指導方針適用於其他語言。  
  
 **X 不**擴充方法放在相同的命名空間擴充的型別，除非它是用於將方法加入至介面或相依性管理。  
  
 **請避免 x**定義兩個或多個使用相同的簽章的擴充方法，即使它們是不同的命名空間中。  
  
 **✓ 考慮**如果類型是介面，並擴充方法的用意是要用於大部分或所有的情況下，擴充的型別相同的命名空間中定義的擴充方法。  
  
 **X 不**定義實作一項功能通常會與其他功能相關聯的命名空間中的擴充方法。 相反地，在其所屬的功能與相關聯的命名空間中進行定義。  
  
 **請避免 x**泛型命名的命名空間專門用來擴充方法 (例如，"Extensions")。 使用描述性名稱 （例如，「 路由 」） 改為。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
