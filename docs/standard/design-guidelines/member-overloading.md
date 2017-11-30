---
title: "成員多載"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b54a99ab88e4cfa0569b2095a0be3750c91f244
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="member-overloading"></a>成員多載
成員多載是指只有不同數目或類型的參數，但具有相同名稱的相同型別上建立兩個或多個成員。 例如，在下列程式碼，`WriteLine`方法多載：  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 因為只有方法、 建構函式和索引的屬性可以有參數，只有那些成員可能會超載。  
  
 多載是其中一個最重要的技術，用於改善可用性、 產能和可重複使用程式庫的可讀性。 多載的參數數目，讓能夠提供更簡單的建構函式和方法的版本。 參數類型多載，可讓使用相同的成員執行相同作業上將選取的不同類型的成員名稱。  
  
 **✓ 不要**試著使用描述性的參數名稱，表示使用較短的多載的預設值。  
  
 **請避免 x**任意改變在多載的參數名稱。 如果一個多載中的參數表示相同的輸入中另一個多載的參數，參數應該是相同的名稱。  
  
 **請避免 x**不一致，在此順序中的參數中的多載成員。 具有相同名稱的參數應該會出現在所有多載中的相同位置。  
  
 **✓ 不要**（如果是必要的擴充性） 進行的最長多載虛擬。 較短的多載應該只是透過呼叫長的多載。  
  
 **X 不**使用`ref`或`out`多載成員的修飾詞。  
  
 某些語言無法將呼叫解析為多載，就像這樣。 此外，這種多載通常有完全不同的語意，而且可能不能多載，但兩個各自方法改為。  
  
 **X 不**具有多載具有位於相同位置和類似的類型參數，但具有不同的語意。  
  
 **✓ 不要**允許`null`為選擇性引數傳遞。  
  
 **✓ 不要**使用成員多載，而不是定義具有預設引數的成員。  
  
 預設引數不符合 CLS 標準。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計指導方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
