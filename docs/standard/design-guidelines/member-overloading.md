---
title: 成員多載
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208227"
---
# <a name="member-overloading"></a>成員多載
成員多載是指的差別只在於參數類型或數目，但具有相同名稱的相同型別上建立兩個或多個成員。 例如，在下列程式碼，`WriteLine`多載方法：  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 只有方法、 建構函式和索引的屬性可以有參數，因為只有這些成員可以多載。  
  
 多載是其中一個最重要的技術改進使用性、 生產力及重複使用程式庫的可讀性。 多載的參數數目，讓能夠提供簡單的建構函式和方法的版本。 參數類型多載，讓能夠使用相同的成員名稱，執行相同的作業，在一組選取的不同類型的成員。  
  
 **✓ DO** 試著使用描述性的參數名稱，表示使用較短的多載的預設值。  
  
 **X AVOID** 任意改變在多載的參數名稱。 如果其中一個多載中的參數代表相同的輸入參數，以在另一個多載，這些參數應該有相同的名稱。  
  
 **X AVOID** 不一致，在此順序中的參數中的多載成員。 具有相同名稱的參數應該會出現在所有多載中的相同位置。  
  
 **✓ DO**（如果是必要的擴充性） 進行的最長多載虛擬。 較短的多載應該只是透過呼叫較長的多載。  
  
 **X DO NOT** 使用 `ref` 或 `out` 多載成員的修飾詞。  
  
 有些語言無法解析這類的多載的呼叫。 此外，這類多載通常有完全不同的語意，而且可能不應該多載，但兩個不同的方法而。  
  
 **X DO NOT** 具有多載具有位於相同位置和類似的類型參數，但具有不同的語意。  
  
 **✓ DO** 允許 `null` 為選擇性引數傳遞。  
  
 **✓ DO** 使用成員多載，而不是定義具有預設引數的成員。  
  
 預設引數不符合 CLS 標準。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
