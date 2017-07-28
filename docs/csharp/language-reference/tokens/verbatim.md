---
title: "@ (C# 參考) | Microsoft Docs"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: c32a3d83730c8e9ba5e74f74a436174294538d95
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="-c-reference"></a>@ (C# 參考)

`@` 特殊字元可用為逐字識別項。 使用方式如下：

1. 讓 C# 關鍵字用為識別項。 `@` 字元將程式碼元素當成前置詞，編譯器要將此元素解譯為識別項，不是 C# 關鍵字。 下例會使用 `@` 字元來定義名為 `for` 的識別項，它會用在 `for` 迴圈中。

   [!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. 表示要逐字解譯字串常值。 這個執行個體中的 `@` 字元會定義「逐字字串常值」。 簡單逸出序列 (例如 `"\\"` 用於反斜線)、十六進位逸出序列 (例如 `"\x0041"` 用於大寫 A)，以及 Unicode 逸出序列 (例如 `"\u0041"` 用於大寫 A) 都是照字面解譯。 只有引號逸出序列 (`""`) 不照字面解譯，它會產生單引號。 下例會定義兩個相同的檔案路徑，一個使用規則字串常值，另一個使用逐字字串常值。 這是逐字字串常值較常見的用法之一。

   [!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   下例示範定義包含相同字元序列的規則字串常值和逐字字串常值的效果。

   [!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. 如果發生命名衝突，讓編譯器區別屬性。 屬性是衍生自 @System.Attribute 的型別。 其型別名稱通常包含尾碼 **Attribute**，雖然編譯器不會強制執行此慣例。 然後，在程式碼中就可以依其完整型別名稱 (例如 `[InfoAttribute]`) 或簡短名稱 (例如 `[Info]`) 參考屬性。 不過，如果兩個簡短的屬性型別名稱完全相同，但一個型別名稱有 **Attribute** 尾碼，一個沒有，即會發生命名衝突。 例如，下列程式碼無法編譯，因為編譯器無法判斷 `Main` 方法套用了 `Info` 或 `InfoAttribute` 屬性。

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   如果逐字識別項用來識別 `Info` 屬性，則範例編譯成功。

   [!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 特殊字元](../../../csharp/language-reference/tokens/index.md)

