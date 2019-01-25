---
title: 巢狀類型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: KrzysztofCwalina
ms.openlocfilehash: 22c14d05105154ff642cb8a44eda8e7c5d0575e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559537"
---
# <a name="nested-types"></a>巢狀類型
巢狀型別是另一個類型，稱為封入類型的範圍內定義的類型。 巢狀型別可以存取其封入類型的所有成員。 比方說，它必須定義在封入類型，以及受保護的欄位定義中的封入類型的所有上階的私用欄位的存取。  
  
 一般情況下，應該謹慎使用巢狀型別。 這有幾個原因。 有些開發人員並不完全熟悉的概念。 這些開發人員，比方說，可能無法使用巢狀型別的變數的宣告語法。 巢狀型別以及其封入類型，也非常緊密結合，並因此不適用於一般用途的型別。  
  
 巢狀型別是最適合用於模型化其封入類型的實作詳細資料。 終端使用者應該幾乎不需要宣告巢狀類型的變數，而且幾乎不應該明確具現化巢狀型別。 例如，集合的列舉值可以是該集合的巢狀的類型。 列舉值通常是具現化依其封入類型，因為許多語言支援 foreach 陳述式，列舉值的變數很少需要使用者宣告。  
  
 **✓ DO** 時的巢狀的類型和其外部型別之間的關聯性，這類成員存取範圍語法是想要使用巢狀型別。  
  
 **X DO NOT** 使用公用巢狀型別做為邏輯群組建構，則使用這個命名空間。  
  
 **X AVOID** 公開巢狀型別。 唯一的例外是如果需要宣告只有在罕見的情況下，例如 subclassing 或其他進階的自訂案例的巢狀類型的變數。  
  
 **X DO NOT** 可能外部包含型別中參考該類型時，使用巢狀型別。  
  
 例如，傳遞至方法，類別中定義的列舉不應該定義為類別中的巢狀類型。  
  
 **X DO NOT** 使用巢狀型別，如果它們必須具現化用戶端程式碼。  如果類型具有公用建構函式，它應該可能不是巢狀。  
  
 如果類型可以具現化，這就好像是指出該類型具有本身的架構中的位置 （您可以建立、 使用，並終結不需使用外部型別），因此應該不是巢狀。 內部的類型應該不能廣泛地重複使用之外沒有任何關聯性的外部型別也為外部型別。  
  
 **X DO NOT** 定義巢狀型別為介面的成員。 許多語言不支援這類建構。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
