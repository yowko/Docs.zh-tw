---
title: 成員多載
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: KrzysztofCwalina
ms.openlocfilehash: 4caa0ae78d168b23fd2862153bef0e3960d3ea42
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392940"
---
# <a name="member-overloading"></a>成員多載
成員多載表示在相同類型上建立兩個或多個成員，但只有參數的數目或類型不同，但具有相同的名稱。 例如，在下列中，會多載 `WriteLine` 方法：  
  
```csharp  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 因為只有方法、函式和索引屬性可以有參數，所以只有那些成員可以多載。  
  
 多載是改善可重複使用之程式庫的可用性、生產力和可讀性的其中一個最重要的技巧。 參數數目的多載可讓您提供更簡單版本的函式和方法。 在參數類型上多載，可以針對在一組選取的不同類型上執行相同作業的成員，使用相同的成員名稱。  
  
 **✓ DO** 試著使用描述性的參數名稱，表示使用較短的多載的預設值。  
  
 **X AVOID** 任意改變在多載的參數名稱。 如果某個多載中的參數表示的輸入與另一個多載中的參數相同，則參數應該具有相同的名稱。  
  
 **X AVOID** 不一致，在此順序中的參數中的多載成員。 具有相同名稱的參數應該會出現在所有多載的相同位置。  
  
 **✓ DO**（如果是必要的擴充性） 進行的最長多載虛擬。 較短的多載應該只呼叫較長的多載。  
  
 **X DO NOT** 使用 `ref` 或 `out` 多載成員的修飾詞。  
  
 有些語言無法解析對多載的呼叫，如下所示。 此外，這類多載通常會有完全不同的語義，而且可能不應該是多載，而是改為兩個不同的方法。  
  
 **X DO NOT** 具有多載具有位於相同位置和類似的類型參數，但具有不同的語意。  
  
 **✓ DO** 允許 `null` 為選擇性引數傳遞。  
  
 **✓ DO** 使用成員多載，而不是定義具有預設引數的成員。  
  
 預設引數不符合 CLS 標準。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 從 @no__t 1Framework 設計指導方針中，@no__t 0Reprinted by 皮耳森教育，Inc. 的許可權：可重複使用的 .NET 程式庫、第2版 @ no__t-0 by Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式，已于2008年10月22日發行，其為 Microsoft Windows 開發系列的一部分 Addison-Wesley Professional。 *  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
