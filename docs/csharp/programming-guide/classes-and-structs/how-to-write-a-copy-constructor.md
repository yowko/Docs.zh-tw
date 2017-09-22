---
title: "如何：撰寫複製建構函式 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 712d9d5e792d025dd7c91d4c1809eeba96759757
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：撰寫複製建構函式 (C# 程式設計手冊)
C\# 不提供物件的複製建構函式，不過，您可以自行撰寫複製建構函式。  
  
## 範例  
 在下列範例中，`Person` [類別](../../../csharp/language-reference/keywords/class.md)會定義接受 `Person` 執行個體做為引數的複製建構函式。  引數的屬性值會指派給新的 `Person` 執行個體的屬性。  程式碼包含替代的複製建構函式，這會傳送您要複製到類別之執行個體建構函式的執行個體的 `Name` 和 `Age` 屬性。  
  
 [!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## 請參閱  
 <xref:System.ICloneable>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)

