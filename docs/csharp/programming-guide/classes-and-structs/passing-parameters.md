---
title: 傳遞參數 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: fec9e0d4af108222ffa62553454b141096702d12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514071"
---
# <a name="passing-parameters-c-programming-guide"></a>傳遞參數 (C# 程式設計手冊)
在 C# 中，引數可以由傳值或傳址方式傳遞至參數。 以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。 若要以傳址方式傳遞參數，且目的是變更該值，請使用 `ref` 或 `out` 關鍵字。 若以傳址方式傳遞之目的是不要發生複製的情況，但不變更該值，請使用 `in` 修飾詞。 為簡化起見，本主題的範例中只使用 `ref` 關鍵字。 如需 `in`、`ref` 與 `out` 之間差異的詳細資訊，請參閱 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 和 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md)。  
  
 下例會說明值和參考參數之間的差異。  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [傳遞實值型別參數](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [傳遞參考型別參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[引數清單](~/_csharplang/spec/expressions.md#argument-lists)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)
