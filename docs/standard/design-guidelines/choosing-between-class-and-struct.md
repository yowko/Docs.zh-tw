---
title: 在類別和結構之間選擇
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bb05b825113c025781a790dc206d500633a3b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573577"
---
# <a name="choosing-between-class-and-struct"></a>在類別和結構之間選擇
其中每個架構設計師所面臨的基本設計決策在於要設計的類型 （參考型別） 的類別或結構 （實值類型）。 充分了解的參考類型和實值類型的行為差異是在選擇非常重要的。  
  
 第一個參考類型和實值類型是參考型別是在堆積上配置和記憶體回收，而實值類型會配置在堆疊上，或在包含內嵌類型，並取消配置時，我們會考慮之間的差異堆疊回溯或當其包含的型別取得已取消配置。 因此，實值類型的配置和解除是參考類型的配置和解除比廉價的一般。  
  
 接下來，陣列的參考型別會配置超出行，這表示的陣列項目是只是在堆積上的參考類型的執行個體參考。 值類型陣列的配置是內嵌，表示陣列元素為實值類型的實際執行個體。 因此，值類型陣列的配置和解除會比參考型別陣列的配置和解除成本更低。 此外，在大部分情況下的值型別陣列會呈現多參考位置較佳。  
  
 下一項差異被與記憶體使用量。 取得 boxed 實值類型，當轉型為參考類型或其中一個所實作的介面。 他們取得 unboxed 時轉型為實值型別。 因為方塊是在堆積上配置和記憶體回收、 過度 boxing 和 unboxing 是物件可以有堆積、 記憶體回收行程，以及最終的應用程式效能的負面影響。  相較之下，當參考類型會轉換，就會不發生任何這類 boxing。  
  
 接下來，指派參考類型，將參考複製，而值的型別指派複製整個值。 因此，大型的參考類型的指派較低的大型值型別指派比。  
  
 最後，參考型別是傳址方式傳遞，而傳值方式傳遞的實值類型。 參考類型的執行個體的變更會影響所有指向執行個體的參考。 依值傳遞時，會複製值類型執行個體。 當實值類型的執行個體變更時，當然不會影響任何其複本。 因為複本不由使用者明確建立，但會以隱含方式建立引數會傳遞或傳回值傳回時，可以變更的實值類型可以是許多使用者造成混淆。 因此，實值型別應該是不變。  
  
 根據經驗法則，大部分的架構中的類型應該是類別。 有，不過，某些情況中的實值類型特性使得較適合使用結構。  
  
 **✓ CONSIDER** 定義而不是類別結構，如果執行個體類型的小，通常存留較短或嵌入其他物件。  
  
 **X AVOID** 定義結構，除非該類型具有所有下列特性：  
  
-   它以邏輯方式表示的單一值，類似於基本類型 (`int`，`double`等。)。  
  
-   它具有執行個體大小小於 16 個位元組。  
  
-   它永遠不變。  
  
-   它不會經常 boxed 處理。  
  
 在其他情況下，您應該做為類別定義您的型別。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
