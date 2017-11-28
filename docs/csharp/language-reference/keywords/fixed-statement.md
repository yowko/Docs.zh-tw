---
title: "fixed 陳述式 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords: fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a>fixed 陳述式 (C# 參考)
`fixed` 陳述式可防止記憶體回收行程重新配置可移動的變數。 `fixed` 陳述式只能用於[不安全](../../../csharp/language-reference/keywords/unsafe.md)的內容中。 `Fixed` 也可用來建立[固定大小緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。  
  
 `fixed` 陳述式會將指標設定為 Managed 變數，並在陳述式執行期間「固定」該變數。 如果未使用 `fixed`，由於記憶體回收可能會意外重新配置變數，因此指向可移動的 Managed 變數沒什麼用處。 C# 編譯器只能讓您將指標指派給 `fixed` 陳述式中的 Managed 變數。  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 您可以使用陣列、字串、固定大小緩衝區或變數位址，來初始化指標。 下列範例說明如何使用變數位址、陣列和字串。 如需固定大小緩衝區的詳細資訊，請參閱[固定大小緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 您可以初始化多個指標，但這些指標必須屬於相同類型。  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 若要初始化不同類型的指標，只要巢狀 `fixed` 陳述式即可，如下列範例所示。  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 執行陳述式中的程式碼之後，任何固定的變數都會取消固定並受限於記憶體回收。 因此，請不要指向 `fixed` 陳述式之外的變數。  
  
> [!NOTE]
>  您無法修改在 fixed 陳述式中初始化的指標。  
  
 在不安全模式中，您可以配置堆疊上的記憶體，這不受限於記憶體回收，因此不需要固定。 如需詳細資訊，請參閱 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)  
 [固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
