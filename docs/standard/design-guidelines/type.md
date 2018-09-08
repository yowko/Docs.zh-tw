---
title: 類型設計方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7fb9964d0e542c0937c55ae65bd88b3f7149fa8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187935"
---
# <a name="type-design-guidelines"></a>類型設計方針
CLR 的觀點而言，有只有兩種型別，參考類型和實值型別，但為了解 framework 設計的討論，除類型分成多個邏輯群組，各有其專屬特定設計規則。  
  
 類別是參考類型的一般情況。 它們會構成大量的大部分的架構中的型別。 類別應該其大受歡迎，它們支援的物件導向功能的豐富，其一般適用性。 基底類別和抽象類別是特殊的邏輯群組，與擴充性。  
  
 介面是參考型別和實值型別都可實作這個型別。 他們因此可做為參考型別和實值型別多型階層的根憑證。 此外，介面可用來模擬原本不支援由 CLR 中的多重繼承。  
  
 結構是實值類型的一般情況下，而且應該是保留供小型的簡單類型，類似於語言基本類型。  
  
 列舉是特殊案例的實值型別用於定義簡短的值，例如週、 主控台色彩等等的天數。  
  
 靜態類別是要作為容器的靜態成員的型別。 它們是通常用來提供其他作業的捷徑。  
  
 委派、 例外狀況、 屬性、 陣列和集合都適用於特定用途，參考類型的所有特殊的情況下，其設計和使用方式的指導方針將於他處討論這個活頁簿中。  
  
 **✓ DO** 確保每個類型的一組妥善定義之相關成員，不只是隨機的不相關的功能集合。  
  
## <a name="in-this-section"></a>本節內容  
 [在類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象類別設計](../../../docs/standard/design-guidelines/abstract-class.md)  
 [靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)  
 [介面設計](../../../docs/standard/design-guidelines/interface.md)  
 [結構設計](../../../docs/standard/design-guidelines/struct.md)  
 [列舉設計](../../../docs/standard/design-guidelines/enum.md)  
 [巢狀型別](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
