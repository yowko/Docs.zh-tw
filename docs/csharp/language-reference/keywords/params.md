---
title: params (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751948"
---
# <a name="params-c-reference"></a>params (C# 參考)
使用 `params` 關鍵字，您可以指定[方法參數](../../../csharp/language-reference/keywords/method-parameters.md)，其採用可變數目的引數。  
  
 您可以傳送在參數宣告或指定型別的引數陣列中指定的型別引數的逗點分隔清單。 您也可以不傳送任何引數。 如果不傳送任何引數，`params` 清單的長度為零。  
  
 在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。  
 
 `params` 參數的宣告類型必須是一維陣列，如下列範例所示。 否則，就會發生編譯器錯誤 [CS0225](../../../csharp/misc/cs0225.md)。
  
## <a name="example"></a>範例  
 下例示範將引數傳送至 `params` 參數的各種方式。  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)
