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
ms.openlocfilehash: af7511f4159fdbfe2d3f972dc927e9ee11fd586f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572885"
---
# <a name="type-design-guidelines"></a>類型設計方針
CLR 觀點中，有類型只有兩個類別，參考類型和實值類型 — 但架構設計的相關討論，為了分割類型分成多個邏輯群組，每個都有它自己的特定設計規則。  
  
 類別是參考類型的一般情況。 它們會構成大量大部分的架構中的型別。 類別在其支援的物件導向的功能集的豐富和一般適用性年末其受歡迎情況看出。 基底類別和抽象類別是特殊的邏輯群組與擴充性。  
  
 介面是由參考類型和實值類型可以實作的類型。 它們可因此做為參考類型和實值型別多型階層的根目錄。 此外，介面可以用來模擬原生不支援由 CLR 中的多重繼承。  
  
 結構是實值類型的一般情況下，以及應該保留小型、 簡單類型，類似於語言基本類型。  
  
 列舉是用來定義簡短組值，例如週、 的主控台色彩等等的天的實值類型的特殊案例。  
  
 靜態類別是要作為容器使用的靜態成員的型別。 它們通常用於提供其他作業的捷徑。  
  
 委派、 例外狀況、 屬性、 陣列和集合的參考型別適用於特定用途，所有的特殊情況下，而且這個活頁簿中已於他處討論設計和使用方式的指導方針。  
  
 **✓ DO** 確保每個類型的一組妥善定義之相關成員，不只是隨機的不相關的功能集合。  
  
## <a name="in-this-section"></a>本節內容  
 [在類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象類別設計](../../../docs/standard/design-guidelines/abstract-class.md)  
 [靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)  
 [介面設計](../../../docs/standard/design-guidelines/interface.md)  
 [結構設計](../../../docs/standard/design-guidelines/struct.md)  
 [列舉設計](../../../docs/standard/design-guidelines/enum.md)  
 [巢狀型別](../../../docs/standard/design-guidelines/nested-types.md)  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
