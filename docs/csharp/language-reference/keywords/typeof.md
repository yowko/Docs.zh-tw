---
title: typeof (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="typeof-c-reference"></a>typeof (C# 參考)
用來取得類型的 `System.Type` 物件。 `typeof` 運算式有下列形式：  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>備註  
 若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 無法多載 `typeof` 運算子。  
  
 `typeof` 運算子也可以用於開放式泛型型別。 在規格中，具有多個型別參數的類型必須具有適當數目的逗號。 下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。 假設方法是 MethodInfo 類型的執行個體︰  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>範例  
 這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。 這取決於所產生數字的儲存需求。  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Type?displayProperty=nameWithType>  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)
