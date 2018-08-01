---
title: 等號比較運算子
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1e5784de277d59c7bc945cbe7b605653eec7bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571013"
---
# <a name="equality-operators"></a>等號比較運算子
本節討論多載等號比較運算子，而是指`operator==`和`operator!=`為等號比較運算子。  
  
 **X DO NOT**的等號比較運算子，但是其中一個多載。  
  
 **✓ DO**確定<xref:System.Object.Equals%2A?displayProperty=nameWithType>和等號比較運算子有完全相同的語意和類似的效能特性。  
  
 這通常表示`Object.Equals`需要覆寫等號比較運算子經過多載。  
  
 **X AVOID**擲回例外狀況，從等號比較運算子。  
  
 例如，傳回 false，如果其中一個引數為 null，而不是擲回`NullReferenceException`。  
  
## <a name="equality-operators-on-value-types"></a>實值類型上的等號比較運算子  
 **✓ DO**多載等號比較運算子實值型別，如果是有意義的等號比較。  
  
 在大部分的程式設計語言中，沒有預設實作的`operator==`實值型別。  
  
## <a name="equality-operators-on-reference-types"></a>參考類型的等號比較運算子  
 **X AVOID**多載可變動參考類型的等號比較運算子。  
  
 許多語言有參考類型的內建的等號比較運算子。 內建運算子通常會實作參考相等，以及預設的行為變更為實值相等時，許多開發人員會感到驚訝。  
  
 因為不變性會讓它更難發現參考相等與值相等性之間的差異，不可變的參考類型以降低這個問題。  
  
 **X AVOID**如果實作可能會大幅低於參考相等的多載參考類型的等號比較運算子。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
