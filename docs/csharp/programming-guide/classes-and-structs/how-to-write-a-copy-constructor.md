---
title: HOW TO：撰寫複製建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: daf0683060d7df5dc5e644b4b84aac3dcdea939f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240680"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>HOW TO：撰寫複製建構函式 (C# 程式設計手冊)
C# 未提供物件的複製建構函式，但您可以自行撰寫一個。  
  
## <a name="example"></a>範例  
 在下列範例中，`Person`[類別](../../../csharp/language-reference/keywords/class.md)定義接受 `Person` 執行個體作為其引數的複製建構函式。 引數的屬性值會指派給新 `Person` 執行個體的屬性。 這個程式碼包含替代的複製建構函式，可將您想要複製之執行個體的 `Name` 和 `Age` 屬性傳送給類別的執行個體建構函式。  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.ICloneable>  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)
