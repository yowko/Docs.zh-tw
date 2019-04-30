---
title: 等號比較運算子
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960327"
---
# <a name="equality-operators"></a>等號比較運算子
本節討論多載等號比較運算子，而是指`operator==`和`operator!=`為等號比較運算子。  
  
 **X DO NOT** 的等號比較運算子，但是其中一個多載。  
  
 **✓ DO** 確定 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子有完全相同的語意和類似的效能特性。  
  
 這通常表示`Object.Equals`必須覆寫等號比較運算子多載。  
  
 **X AVOID** 擲回例外狀況，從等號比較運算子。  
  
 例如，如果傳回 false 其中一個引數為 null 而非擲回`NullReferenceException`。  
  
## <a name="equality-operators-on-value-types"></a>實值型別上的等號比較運算子  
 **✓ DO** 多載等號比較運算子實值型別，如果是有意義的等號比較。  
  
 在大部分的程式設計語言，不會有預設實作的`operator==`實值型別。  
  
## <a name="equality-operators-on-reference-types"></a>參考型別上的等號比較運算子  
 **X AVOID** 多載可變動參考類型的等號比較運算子。  
  
 許多語言有參考類型的內建的等號比較運算子。 內建運算子通常會實作參考相等，並預設行為變更為實值相等時，許多開發人員都會很驚訝。  
  
 不可變的參考型別降低這個問題，因為不變性讓更難發現參考相等與實值相等之間的差異。  
  
 **X AVOID** 如果實作可能會大幅低於參考相等的多載參考類型的等號比較運算子。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
