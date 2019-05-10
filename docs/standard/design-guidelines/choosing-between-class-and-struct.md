---
title: 在類別和結構之間選擇
ms.date: 10/22/2008
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
author: KrzysztofCwalina
ms.openlocfilehash: 5041368ca1a440698c399c935ac72aba2002c3ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615272"
---
# <a name="choosing-between-class-and-struct"></a>在類別和結構之間選擇
每個 framework 設計工具所面臨的基本設計決策之一是設計為型別，做為類別 （參考型別） 或結構 （實值型別）。 深入了解的參考型別和實值類型的行為差異是非常重要的做此選擇。  
  
 第一個參考型別和實值型別是參考型別在堆積上配置和回收，則實值型別會配置在堆疊上，或包含內嵌類型，並解除配置時，我們會考慮之間的差異堆疊回溯時或當其包含的型別取得已取消配置。 因此，實值類型的配置和解除會比參考類型的配置和解除便宜的一般。  
  
 接下來，參考類型的陣列配置外行，這表示的陣列項目是只在堆積上的參考類型的執行個體的參考。 值型別陣列的配置是內嵌，這表示陣列項目實值型別的實際的執行個體。 因此，值型別陣列的配置和解除會比參考型別陣列的配置和解除成本更低。 此外，在大多數情況下值型別陣列顯現出更好的參考位置。  
  
 下一項差異被與記憶體使用量。 取得 boxed 實值型別，當轉換成參考型別或其中一個所實作的介面。 他們會收到 unboxed 時轉換回實值型別。 因為方塊是在堆積上配置，而且會回收，太多 boxing 和 unboxing 的物件可以有堆積、 記憶體回收行程，以及最終的應用程式效能的負面影響。  相反地，當參考型別會轉換，就會不發生任何這類 boxing。 (如需詳細資訊，請參閱 < [Boxing 和 Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md))。
  
 接下來，參考型別指派會複製參考，而值的型別指派會複製整個值。 因此，大型的參考類型的指派成本較低的大型值型別指派比。  
  
 最後，參考型別是傳址方式傳遞，而由值傳遞實值型別。 參考類型的執行個體的變更會影響所有指向執行個體的參考。 依值傳遞時，會複製值型別執行個體。 變更的實值型別執行個體時，它當然不會影響任何其複本。 因為複本不由使用者明確建立，但隱含建立引數會傳遞或傳回值傳回時，可以變更的實值型別可以是許多使用者造成混淆。 因此，實值型別應該是不可變的。  
  
 根據經驗法則，大部分的架構中的類型應該是類別。 有，不過，某些情況中實值類型的特性讓它更適合使用結構。  
  
 **✓ CONSIDER** 定義而不是類別結構，如果執行個體類型的小，通常存留較短或嵌入其他物件。  
  
 **X AVOID** 定義結構，除非該類型具有所有下列特性：  
  
- 它以邏輯方式表示的單一值，類似於基本型別 (`int`， `double`，依此類推。)。  
  
- 它具有執行個體大小小於 16 個位元組。  
  
- 它永遠不變。  
  
- 它不會經常 boxed。  
  
 在其他情況下，您應該做為類別定義您的型別。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
