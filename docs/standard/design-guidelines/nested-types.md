---
title: "巢狀類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ae09df49b97cc2fe84285c3a37e1562da185f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types"></a>巢狀類型
巢狀型別是另一個類型，稱為封入類型的範圍內定義的類型。 巢狀型別可以存取其封入類型的所有成員。 例如，具有存取權給定義在封入類型，以及受保護的定義中封入類型的所有上階欄位的私用欄位。  
  
 一般情況下，就應該謹慎巢狀型別。 這有幾個原因。 有些開發人員並不完全熟悉概念。 這些開發人員可能會比方說，有巢狀類型的變數的宣告語法問題。 巢狀型別也非常緊密結合其封入類型，並在這種情況不適合一般用途的型別。  
  
 巢狀型別是最適合用來建立模型及其封入類型的實作詳細資料。 終端使用者應該很少需要宣告巢狀類型的變數，而幾乎永遠都不應該需要明確具現化巢狀型別。 例如，集合的列舉值可以是該集合的巢狀的類型。 通常會依其封入類型具現化列舉值，因為許多語言都支援 foreach 陳述式，列舉值的變數很少需要使用者宣告。  
  
 **✓ 不要**時的巢狀的類型和其外部型別之間的關聯性，這類成員存取範圍語法是想要使用巢狀型別。  
  
 **X 不**使用公用巢狀型別做為邏輯群組建構，則使用這個命名空間。  
  
 **請避免 x**公開巢狀型別。 唯一的例外是如果需要宣告只有在極少數的情況下，例如 subclassing 或其他進階的自訂案例的巢狀類型的變數。  
  
 **X 不**可能外部包含型別中參考該類型時，使用巢狀型別。  
  
 例如，傳遞至方法，在類別定義列舉不應定義為類別中的巢狀類型。  
  
 **X 不**使用巢狀型別，如果它們必須具現化用戶端程式碼。  如果類型具有公用建構函式，它應該可能不是巢狀。  
  
 如果型別可以具現化，這好像來表示型別具有自己的架構中的位置 （您可以建立、 使用它，和摧毀不需使用外部型別），因此應該不巢狀。 內部的類型應該不能廣泛地重複使用外部型別，如果沒有任何關聯性外部擔保外部型別。  
  
 **X 不**定義巢狀型別為介面的成員。 許多語言不支援這類建構。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [型別設計指導方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
